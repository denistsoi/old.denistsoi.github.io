---
layout: post
title: "getting started with golang part 5"
description: ""
category: 
tags: [GOLANG, GOLANG SLICES]
excerpt: 
---
{% include JB/setup %}

### Lesson 31  
[GO ARRAYS](http://tour.golang.org/#31)

    package main

    import "fmt"

    func main() {
        var a [2]string
        a[0] = "Hello"
        a[1] = "World"
        fmt.Println(a[0], a[1])
        fmt.Println(a)
    }

    RETURNS: 
    Hello World
    [Hello World]


The type [n]T is an array of n values of type T.

The expression
var a [10]int
declares a variable a as an array of ten integers.

An array's length is part of its type, so arrays cannot be resized. This seems limiting, but don't worry; Go provides a convenient way of working with arrays.

Moving On

### Lesson 32  
[GO SLICES](http://tour.golang.org/#32)

    package main

    import "fmt"

    func main() {
        p := []int{2, 3, 5, 7, 11, 13}
        fmt.Println("p ==", p)

        for i := 0; i < len(p); i++ {
            fmt.Printf("p[%d] == %d\n", i, p[i])
        }
    }

A slice points to an array of values and also includes a length.
[]T is a slice with elements of type T.

THOUGHT: Can we put a function for fetching values to instantiate values for array~

Moving On

### Lesson 33  
[GO SLICIING SLICES](http://tour.golang.org/#33)

    package main

    import "fmt"

    func main() {
        p := []int{2, 3, 5, 7, 11, 13}
        fmt.Println("p ==", p)
        fmt.Println("p[1:4] ==", p[1:4])

        // missing low index implies 0
        fmt.Println("p[:3] ==", p[:3])

        // missing high index implies len(s)
        fmt.Println("p[4:] ==", p[4:])
    }
    RETURNS: 
    p == [2 3 5 7 11 13]
    p[1:4] == [3 5 7]
    p[:3] == [2 3 5]
    p[4:] == [11 13]

Slices can be re-sliced, creating a new slice value that points to the same array.

The expression

s[lo:hi]
evaluates to a slice of the elements from lo through hi-1, inclusive. Thus

s[lo:lo]
is empty and

s[lo:lo+1]
has one element.

THOUGHT: SIMILAR TO PYTHON and Slice in Jquery?

NOTE: basically, 
if p[1:4], the returned values are index, 1 -> 3 (totalling 3 values)
if p[0:3], the returned values are index, 0 -> 2 (totalling 3 values)
if p[4:],  the returned values are index, 4 -> end (totalling 2 values)

Moving On

### Lesson 34  
[GO MAKING MORE SLICES](http://tour.golang.org/#34)

    package main

    import "fmt"

    func main() {
        a := make([]int, 5)
        printSlice("a", a)
        b := make([]int, 0, 5)
        printSlice("b", b)
        c := b[:2]
        printSlice("c", c)
        d := c[2:5]
        printSlice("d", d)
    }

    func printSlice(s string, x []int) {
        fmt.Printf("%s len=%d cap=%d %v\n",
            s, len(x), cap(x), x)
    }

Slices are created with the make function. It works by allocating a zeroed array and returning a slice that refers to that array:

a := make([]int, 5)  // len(a)=5
To specify a capacity, pass a third argument to make:

b := make([]int, 0, 5) // len(b)=0, cap(b)=5

b = b[:cap(b)] // len(b)=5, cap(b)=5
b = b[1:]      // len(b)=4, cap(b)=4

NOTE: Slices made via the make function can allow limit and capacity for the slices made~

Moving on

### Lesson 35  
[GO NIL SLICES](http://tour.golang.org/#35)

    package main

    import "fmt"

    func main() {
        var z []int
        fmt.Println(z, len(z), cap(z))
        if z == nil {
            fmt.Println("nil!")
        }
    }

The zero value of a slice is nil.

A nil slice has a length and capacity of 0.

(To learn more about slices, read the [Slices: usage and internals article.](http://blog.golang.org/go-slices-usage-and-internals))

Moving on

### Lesson 36  
[GO RANGE](http://tour.golang.org/#35)

    package main

    import "fmt"

    var pow = []int{1, 2, 4, 8, 16, 32, 64, 128}

    func main() {
        for i, v := range pow {
            fmt.Printf("2**%d = %d\n", i, v)
        }
    }

The range form of the for loop iterates over a slice or map.

NOTE: 
- for range? 
- i = index
- v = value

Range Cont.

    package main

    import "fmt"

    func main() {
        pow := make([]int, 10)
        for i := range pow {
            pow[i] = 1 << uint(i)
        }
        for _, value := range pow {
            fmt.Printf("%d\n", value)
        }
    }

You can skip the index or value by assigning to _.

If you only want the index, drop the ", value" entirely.

NOTE:
- what is "<<"?
- what is uint( )?

END OF PART 5