---
layout: post
title: "golang exercises"
description: ""
category: 
tags: [GOLANG, GOLANG EXERCISES]
excerpt: 
---
{% include JB/setup %}

[Complex Cube Roots](http://tour.golang.org/#50)

    package main

    import (
        "fmt" 
        "math"
    )

    func Cbrt(x float64) float64 {
        Pow(x,y)
        return x
    }

    func main() {
        fmt.Println(Cbrt(2))
    }


Let's explore Go's built-in support for complex numbers via the complex64 and complex128 types. For cube roots, Newton's method amounts to repeating:

Find the cube root of 2, just to make sure the algorithm works. There is a Pow function in the math/cmplx package.

[Errors](http://tour.golang.org/#58)

    package main

    import (
        "fmt"
    )

    func Sqrt(f float64) (float64, error) {
        return 0, nil
    }

    func main() {
        fmt.Println(Sqrt(2))
        fmt.Println(Sqrt(-2))
    }

Copy your Sqrt function from the earlier exercises and modify it to return an error value.

Sqrt should return a non-nil error value when given a negative number, as it doesn't support complex numbers.

Create a new type

type ErrNegativeSqrt float64
and make it an error by giving it a

func (e ErrNegativeSqrt) Error() string
method such that ErrNegativeSqrt(-2).Error() returns "cannot Sqrt negative number: -2".

Note: a call to fmt.Print(e) inside the Error method will send the program into an infinite loop. You can avoid this by converting e first: fmt.Print(float64(e)). Why?

Change your Sqrt function to return an ErrNegativeSqrt value when given a negative number.

[HTTP Handlers](http://tour.golang.org/#60)

    package main

    import (
        "net/http"
    )

    func main() {
        // your http.Handle calls here
        http.ListenAndServe("localhost:4000", nil)
    }

Implement the following types and define ServeHTTP methods on them. Register them to handle specific paths in your web server.

    type String string

    type Struct struct {
        Greeting string
        Punct    string
        Who      string
    }

For example, you should be able to register handlers using:

    http.Handle("/string", String("I'm a frayed knot."))
    http.Handle("/struct", &Struct{"Hello", ":", "Gophers!"})

[IMAGES](http://tour.golang.org/#62)

    package main

    import (
        "code.google.com/p/go-tour/pic"
        "image"
    )

    type Image struct{}

    func main() {
        m := Image{}
        pic.ShowImage(m)
    }

Remember the picture generator you wrote earlier? Let's write another one, but this time it will return an implementation of image.Image instead of a slice of data.

Define your own Image type, implement the necessary methods, and call pic.ShowImage.

Bounds should return a image.Rectangle, like image.Rect(0, 0, w, h).

ColorModel should return color.RGBAModel.

At should return a color; the value v in the last picture generator corresponds to color.RGBA{v, v, 255, 255} in this one.

[EQUIVALENT BINARY TREES](http://tour.golang.org/#72)

    package main

    import "code.google.com/p/go-tour/tree"

    // Walk walks the tree t sending all values
    // from the tree to the channel ch.
    func Walk(t *tree.Tree, ch chan int)

    // Same determines whether the trees
    // t1 and t2 contain the same values.
    func Same(t1, t2 *tree.Tree) bool

    func main() {
    }

1. Implement the Walk function.

2. Test the Walk function.

The function tree.New(k) constructs a randomly-structured binary tree holding the values k, 2k, 3k, ..., 10k.

Create a new channel ch and kick off the walker:

go Walk(tree.New(1), ch)
Then read and print 10 values from the channel. It should be the numbers 1, 2, 3, ..., 10.

3. Implement the Same function using Walk to determine whether t1 and t2 store the same values.

4. Test the Same function.

Same(tree.New(1), tree.New(1)) should return true, and Same(tree.New(1), tree.New(2)) should return false.

[WEB CRAWLER](http://tour.golang.org/#73)

    package main

    import (
        "fmt"
    )

    type Fetcher interface {
        // Fetch returns the body of URL and
        // a slice of URLs found on that page.
        Fetch(url string) (body string, urls []string, err error)
    }

    // Crawl uses fetcher to recursively crawl
    // pages starting with url, to a maximum of depth.
    func Crawl(url string, depth int, fetcher Fetcher) {
        // TODO: Fetch URLs in parallel.
        // TODO: Don't fetch the same URL twice.
        // This implementation doesn't do either:
        if depth <= 0 {
            return
        }
        body, urls, err := fetcher.Fetch(url)
        if err != nil {
            fmt.Println(err)
            return
        }
        fmt.Printf("found: %s %q\n", url, body)
        for _, u := range urls {
            Crawl(u, depth-1, fetcher)
        }
        return
    }

    func main() {
        Crawl("http://golang.org/", 4, fetcher)
    }

    // fakeFetcher is Fetcher that returns canned results.
    type fakeFetcher map[string]*fakeResult

    type fakeResult struct {
        body string
        urls []string
    }

    func (f fakeFetcher) Fetch(url string) (string, []string, error) {
        if res, ok := f[url]; ok {
            return res.body, res.urls, nil
        }
        return "", nil, fmt.Errorf("not found: %s", url)
    }

    // fetcher is a populated fakeFetcher.
    var fetcher = fakeFetcher{
        "http://golang.org/": &fakeResult{
            "The Go Programming Language",
            []string{
                "http://golang.org/pkg/",
                "http://golang.org/cmd/",
            },
        },
        "http://golang.org/pkg/": &fakeResult{
            "Packages",
            []string{
                "http://golang.org/",
                "http://golang.org/cmd/",
                "http://golang.org/pkg/fmt/",
                "http://golang.org/pkg/os/",
            },
        },
        "http://golang.org/pkg/fmt/": &fakeResult{
            "Package fmt",
            []string{
                "http://golang.org/",
                "http://golang.org/pkg/",
            },
        },
        "http://golang.org/pkg/os/": &fakeResult{
            "Package os",
            []string{
                "http://golang.org/",
                "http://golang.org/pkg/",
            },
        },
    }

In this exercise you'll use Go's concurrency features to parallelize a web crawler.

Modify the Crawl function to fetch URLs in parallel without fetching the same URL twice.