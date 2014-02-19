---
layout: post
title: "getting started with golang part 9"
description: ""
category: 
tags: []
excerpt: 
---
{% include JB/setup %}

### LESSON 57
[GO ERRORS](http://tour.golang.org/#57)

    package main

    import (
        "fmt"
        "time"
    )

    type MyError struct {
        When time.Time
        What string
    }

    func (e *MyError) Error() string {
        return fmt.Sprintf("at %v, %s",
            e.When, e.What)
    }

    func run() error {
        return &MyError{
            time.Now(),
            "it didn't work",
        }
    }

    func main() {
        if err := run(); err != nil {
            fmt.Println(err)
        }
    }

An error is anything that can describe itself as an error string. The idea is captured by the predefined, built-in interface type, error, with its single method, Error, returning a string:

    type error interface {
        Error() string
    }

The fmt package's various print routines automatically know to call the method when asked to print an error.

### LESSON 59
[GO WEB SERVER](http://tour.golang.org/#59)

    package main

    import (
        "fmt"
        "net/http"
    )

    type Hello struct{}

    func (h Hello) ServeHTTP(
        w http.ResponseWriter,
        r *http.Request) {
        fmt.Fprint(w, "Hello!")
    }

    func main() {
        var h Hello
        http.ListenAndServe("localhost:4000", h)
    }

Package http serves HTTP requests using any value that implements http.Handler:

    package http

    type Handler interface {
        ServeHTTP(w ResponseWriter, r *Request)
    }

In this example, the type Hello implements http.Handler.

Visit http://localhost:4000/ to see the greeting.

Note: This example won't run through the web-based tour user interface. To try writing web servers you may want to Install Go.

### LESSON 61
[GO IMAGES](http://tour.golang.org/#61)

    package main

    import (
        "fmt"
        "image"
    )

    func main() {
        m := image.NewRGBA(image.Rect(0, 0, 100, 100))
        fmt.Println(m.Bounds())
        fmt.Println(m.At(0, 0).RGBA())
    }

Package image defines the Image interface:

    package image

    type Image interface {
        ColorModel() color.Model
        Bounds() Rectangle
        At(x, y int) color.Color
    }

(See the documentation for all the details.)

Also, color.Color and color.Model are interfaces, but we'll ignore that by using the predefined implementations color.RGBA and color.RGBAModel. These interfaces and types are specified by the image/color package