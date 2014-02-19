---
layout: post
title: "getting started with golang part 7"
description: ""
category: 
tags: [GOLANG, GOLANG SWITCH]
excerpt: 
---
{% include JB/setup %}

### Lesson 47  
[GO SWITCH](http://tour.golang.org/#47)

    package main

    import (
        "fmt"
        "runtime"
    )

    func main() {
        fmt.Print("Go runs on ")
        switch os := runtime.GOOS; os {
        case "darwin":
            fmt.Println("OS X.")
        case "linux":
            fmt.Println("Linux.")
        default:
            // freebsd, openbsd,
            // plan9, windows...
            fmt.Printf("%s.", os)
        }
    }

NO breaks in switches (they are automatic), however, if you require two cases to be the same, you could use the __fallthrough__ statement.

Moving on

    package main

    import (
        "fmt"
        "time"
    )

    func main() {
        fmt.Println("When's Saturday?")
        today := time.Now().Weekday()
        switch time.Saturday {
        case today + 0:
            fmt.Println("Today.")
        case today + 1:
            fmt.Println("Tomorrow.")
        case today + 2:
            fmt.Println("In two days.")
        default:
            fmt.Println("Too far away.")
        }
    }

Switch cases evaluate cases from top to bottom, stopping when a case succeeds.

(For example,

    switch i {
    case 0:
    case f():
    }
    does not call f if i==0.)

Note: Time in the Go playground always appears to start at 2009-11-10 23:00:00 UTC, a value whose significance is left as an exercise for the reader.


    package main

    import (
        "fmt"
        "time"
    )

    func main() {
        t := time.Now()
        switch {
        case t.Hour() < 12:
            fmt.Println("Good morning!")
        case t.Hour() < 17:
            fmt.Println("Good afternoon.")
        default:
            fmt.Println("Good evening.")
        }
    }

Switch without a condition is the same as switch true.
This construct can be a clean way to write long if-then-else chains.