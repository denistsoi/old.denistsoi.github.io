---
layout: post
title: "getting started with golang part 8"
description: ""
category: 
tags: [GOLANG, GOLANG METHODS, GOLANG INTERFACES]
excerpt: 
---
{% include JB/setup %}

### Methods and Interfaces

### LESSON 52
[GO Methods and Interfaces](http://tour.golang.org/#52)

    package main

    import (
        "fmt"
        "math"
    )

    type Vertex struct {
        X, Y float64
    }

    func (v *Vertex) Abs() float64 {
        return math.Sqrt(v.X*v.X + v.Y*v.Y)
    }

    func main() {
        v := &Vertex{3, 4}
        fmt.Println(v.Abs())
    }

Go does not have classes. However, you can define methods on struct types.
The method receiver appears in its own argument list between the func keyword and the method name.

    package main

    import (
        "fmt"
        "math"
    )

    type MyFloat float64

    func (f MyFloat) Abs() float64 {
        if f < 0 {
            return float64(-f)
        }
        return float64(f)
    }

    func main() {
        f := MyFloat(-math.Sqrt2)
        fmt.Println(f.Abs())
    }

In fact, you can define a method on any type you define in your package, not just structs.
You cannot define a method on a type from another package, or on a basic type.

    package main

    import (
        "fmt"
        "math"
    )

    type Vertex struct {
        X, Y float64
    }

    func (v *Vertex) Scale(f float64) {
        v.X = v.X * f
        v.Y = v.Y * f
    }

    func (v *Vertex) Abs() float64 {
        return math.Sqrt(v.X*v.X + v.Y*v.Y)
    }

    func main() {
        v := &Vertex{3, 4}
        v.Scale(5)
        fmt.Println(v, v.Abs())
    }

Methods can be associated with a named type or a pointer to a named type.

We just saw two Abs methods. One on the `*Vertex` pointer type and the other on the MyFloat value type.

There are two reasons to use a pointer receiver. First, to avoid copying the value on each method call (more efficient if the value type is a large struct). Second, so that the method can modify the value that its receiver points to.

Try changing the declarations of the Abs and Scale methods to use Vertex as the receiver, instead of `*Vertex.`

The Scale method has no effect when v is a Vertex. Scale mutates v. When v is a value (non-pointer) type, the method sees a copy of the Vertex and cannot mutate the original value.

Abs works either way. It only reads v. It doesn't matter whether it is reading the original value (through a pointer) or a copy of that value.

### LESSON 55
[GO Interfaces](http://tour.golang.org/#55)

    package main

    import (
        "fmt"
        "math"
    )

    type Abser interface {
        Abs() float64
    }

    func main() {
        var a Abser
        f := MyFloat(-math.Sqrt2)
        v := Vertex{3, 4}

        a = f  // a MyFloat implements Abser
        a = &v // a *Vertex implements Abser

        // In the following line, v is a Vertex (not *Vertex)
        // and does NOT implement Abser.
        a = v

        fmt.Println(a.Abs())
    }

    type MyFloat float64

    func (f MyFloat) Abs() float64 {
        if f < 0 {
            return float64(-f)
        }
        return float64(f)
    }

    type Vertex struct {
        X, Y float64
    }
    func (v *Vertex) Abs() float64 {
        return math.Sqrt(v.X*v.X + v.Y*v.Y)
    }

An interface type is defined by a set of methods.  
A value of interface type can hold any value that implements those methods.  
Note: The code on the left fails to compile.  
Vertex doesn't satisfy Abser because the Abs method is defined only on `*Vertex, not Vertex.`

    package main

    import (
        "fmt"
        "os"
    )

    type Reader interface {
        Read(b []byte) (n int, err error)
    }

    type Writer interface {
        Write(b []byte) (n int, err error)
    }

    type ReadWriter interface {
        Reader
        Writer
    }

    func main() {
        var w Writer

        // os.Stdout implements Writer
        w = os.Stdout

        fmt.Fprintf(w, "hello, writer\n")
    }
    
A type implements an interface by implementing the methods.

There is no explicit declaration of intent.

Implicit interfaces decouple implementation packages from the packages that define the interfaces: neither depends on the other.

It also encourages the definition of precise interfaces, because you don't have to find every implementation and tag it with the new interface name.

Package io defines Reader and Writer; you don't have to.