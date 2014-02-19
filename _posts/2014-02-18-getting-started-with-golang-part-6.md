---
layout: post
title: "getting started with golang part 6"
description: ""
category: 
tags: [GOLANG, GOLANG MAPS]
excerpt: 
---
{% include JB/setup %}


### Lesson 39  
[GO MAPS](http://tour.golang.org/#39)

    package main

    import "fmt"

    type Vertex struct {
        Lat, Long float64
    }

    var m map[string]Vertex

    func main() {
        m = make(map[string]Vertex)
        m["Bell Labs"] = Vertex{
            40.68433, -74.39967,
        }
        fmt.Println(m["Bell Labs"])
    }

A map maps keys to values.

Maps must be created with make (not new) before use; the nil map is empty and cannot be assigned to.

### Lesson 40  
[GO MAP LITERALS](http://tour.golang.org/#40)

    package main

    import "fmt"

    type Vertex struct {
        Lat, Long float64
    }

    var m = map[string]Vertex{
        "Bell Labs": Vertex{
            40.68433, -74.39967,
        },
        "Google": Vertex{
            37.42202, -122.08408,
        },
    }

    func main() {
        fmt.Println(m)
    }

Map literals are like struct literals, but the keys are required.

### Lesson 41  
[GO MAP MUTATIONS](http://tour.golang.org/#41)

    package main

    import "fmt"

    type Vertex struct {
        Lat, Long float64
    }

    var m = map[string]Vertex{
        "Bell Labs": {40.68433, -74.39967},
        "Google":    {37.42202, -122.08408},
    }

    func main() {
        fmt.Println(m)
    }

If the top-level type is just a type name, you can omit it from the elements of the literal.



    package main

    import "fmt"

    func main() {
        m := make(map[string]int)

        m["Answer"] = 42
        fmt.Println("The value:", m["Answer"])

        m["Answer"] = 48
        fmt.Println("The value:", m["Answer"])

        delete(m, "Answer")
        fmt.Println("The value:", m["Answer"])

        v, ok := m["Answer"]
        fmt.Println("The value:", v, "Present?", ok)
    }

Insert or update an element in map m:

    m[key] = elem  

Retrieve an element:

    elem = m[key]

Delete an element:

    delete(m, key)

Test that a key is present with a two-value assignment:

    elem, ok = m[key]

If key is in m, ok is true. If not, ok is false and elem is the zero value for the map's element type.

Similarly, when reading from a map if the key is not present the result is the zero value for the map's element type.

### Lesson 44  
[GO FUNCTION VALUES](http://tour.golang.org/#44)

    package main

    import (
        "fmt"
        "math"
    )

    func main() {
        hypot := func(x, y float64) float64 {
            return math.Sqrt(x*x + y*y)
        }

        fmt.Println(hypot(3, 4))
    }

### Lesson 45  
[GO FUNCTION CLOSURES](http://tour.golang.org/#45)

    package main

    import "fmt"

    func adder() func(int) int {
        sum := 0
        return func(x int) int {
            sum += x
            return sum
        }
    }

    func main() {
        pos, neg := adder(), adder()
        for i := 0; i < 10; i++ {
            fmt.Println(
                pos(i),
                neg(-2*i),
            )
        }
    }

Go functions may be closures. A closure is a function value that references variables from outside its body. The function may access and assign to the referenced variables; in this sense the function is "bound" to the variables.

For example, the adder function returns a closure. Each closure is bound to its own sum variable.

### Lesson 46  
[GO FIBONACCI](http://tour.golang.org/#46)

    package main

    import "fmt"

    // fibonacci is a function that returns
    // a function that returns an int.

    func fibonacci() func() int {
        
    }

    func main() {
        f := fibonacci()
        for i := 0; i < 10; i++ {
        }
    }

#### Answer  

    package main

    import "fmt"

    // fibonacci is a function that returns
    // a function that returns an int.

    func fibonacci() func() int {
        x := 0
        y := 1
        
        return func() int {
            x,y = y,x+y
            return x
        }
    }

    func main() {
        f := fibonacci()
        for i := 0; i < 10; i++ {
            fmt.Println(i, f())
        }
    }

Why? - 