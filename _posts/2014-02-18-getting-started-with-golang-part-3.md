---
layout: post
title: "getting started with golang part 3"
description: ""
category: 
tags: [GOLANG, GOLANG IF]
excerpt: 
---
{% include JB/setup %}

### Lesson 22  
[GO IF](http://tour.golang.org/#22)

Remember that the ( ) is not required~

    package main

    import (
        "fmt"
        "math"
    )

    func sqrt(x float64) string {
        if x < 0 {
            return sqrt(-x) + "i"
        }
        return fmt.Sprint(math.Sqrt(x))
    }

    func main() {
        fmt.Println(sqrt(2), sqrt(-4))
    }

Shorthand IF

    package main

    import (
        "fmt"
        "math"
    )

    func pow(x, n, lim float64) float64 {
        if v := math.Pow(x, n); v < lim {
            return v
        }
        return lim
    }

    func main() {
        fmt.Println(
            pow(3, 2, 10),
            pow(3, 3, 20),
        )
    }

Like for, the if statement can start with a short statement to execute before the condition.

Variables declared by the statement are only in scope until the end of the if.

(Try using v in the last return statement.) 
NOTE: v will be returned as undefined~

Moving On


### Lesson 24  
[GO IF ELSE](http://tour.golang.org/#24)

    package main

    import (
        "fmt"
        "math"
    )

    func pow(x, n, lim float64) float64 {
        if v := math.Pow(x, n); v < lim {
            return v
        } else {
            fmt.Printf("%g >= %g\n", v, lim)
        }
        // can't use v here, though
        return lim
    }

    func main() {
        fmt.Println(
            pow(3, 2, 10),
            pow(3, 3, 20),
        )
    }

Variables declared inside an if short statement are also available inside any of the else blocks.

this function is determining if the value v is greater than the limit, and if it is less than the limit, the return value will be v and the limit.
if the value is greater than the limit then the return print out will be "v >= lim"

Moving on