---
layout: post
title: "getting started with golang part 4"
description: ""
category: 
tags: [GOLANG, GOLAND STRUCT]
excerpt: 
---
{% include JB/setup %}

### Lesson 26  
[GO STRUCT](http://tour.golang.org/#26)

    package main

    import "fmt"

    type Vertex struct {
        X int
        Y int
    }

    func main() {
        fmt.Println(Vertex{1, 2})
    }

A struct is a collection of fields.

(And a type declaration does what you'd expect.)

STRUCT FIELDS can be accessed with dot notation

i.e. 
if v := Vertex{1,2} where v.X = 4,
this will result in X = 4 and Y = 2

### Lesson 28  
[GO POINTERS](http://tour.golang.org/#28)

    package main

    import "fmt"

    type Vertex struct {
        X int
        Y int
    }

    func main() {
        p := Vertex{1, 2}
        q := &p
        q.X = 1e9
        fmt.Println(p)
    }

Go has pointers, but no pointer arithmetic.

Struct fields can be accessed through a struct pointer. The indirection through the pointer is transparent.

NOTE: so the pointer q, which points to struct p assigns value X from pointer q with q.X to equal 1e9;

HOMEWORK: WHAT ARE POINTER ARITHMETIC?!

### Lesson 29  
[GO STRUCT LITERALS](http://tour.golang.org/#29)

    package main

    import "fmt"

    type Vertex struct {
        X, Y int
    }

    var (
        p = Vertex{1, 2}  // has type Vertex
        q = &Vertex{1, 2} // has type *Vertex
        r = Vertex{X: 1}  // Y:0 is implicit
        s = Vertex{}      // X:0 and Y:0
    )

    func main() {
        fmt.Println(p, q, r, s)
    }


    RETURNS: {1 2} &{1 2} {1 0} {0 0}

A struct literal denotes a newly allocated struct value by listing the values of its fields.
You can list just a subset of fields by using the Name: syntax. (And the order of named fields is irrelevant.)
The special prefix & constructs a pointer to a newly allocated struct.

NOTE: What happens when we declare p,q,r & s inside func main?
 - Return value is the same~


    package main

    import "fmt"

    type Vertex struct {
        X, Y int
    }

    var (
        p = Vertex{1, 2}  // has type Vertex
        q = &Vertex{1, 2} // has type *Vertex
        r = Vertex{X: 1}  // Y:0 is implicit
        s = Vertex{}      // X:0 and Y:0
    )

    func main() {
        p := Vertex{1, 3}  // has type Vertex
        q := &p
        
        r := p
        r.Y = 6        // Y:0 is implicit
        
        s := Vertex{}      // X:0 and Y:0
        fmt.Println(p, q, r, s)
    }

    RETURNS: {1 3} &{1 3} {1 6} {0 0}

EXPLAINATION: 
p = type Vertex with X=1, Y=3
q = pointer pointing to p
r = p
r.Y = 6

Since r is not a pointer, our value of r.Y is changed to 6 unaffecting other pointers and p.
however, if
r := &p
and r.Y = 6, then all associated values for p.Y is assigned 6.

Moving on

### Lesson 30  
[GO NEW FUNCTION](http://tour.golang.org/#30)

    package main

    import "fmt"

    type Vertex struct {
        X, Y int
    }

    func main() {
        v := new(Vertex)
        fmt.Println(v)
        v.X, v.Y = 11, 9
        fmt.Println(v)
    }

This prints
    &{0 0}
    &{11 9}

Why? - as v is new Vertex with implicit values set to 0... but why the ampersand notation?

REASON:
The expression new(T) allocates a zeroed T value and returns a pointer to it.

    var t *T = new(T)
or
    t := new(T)

Moving On

END OF PART 4: STRUCT