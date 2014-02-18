---
layout: post
title: "getting started with golang part 2"
description: ""
category: 
tags: [GOLANG, GOLANG LOOPS, GOLANG VAR]
excerpt: 
---
{% include JB/setup %}

Part 2

### Lesson 11
[GO VARABLES](http://tour.golang.org/#11)  

    package main

    import "fmt"

    var i int
    var c, python, java bool

    func main() {
        fmt.Println(i, c, python, java)
    }

The `var` statement declares a list of variables; as in function argument lists, the type is last.

ORDER: 'var' > name > 'type'

The above would print 
    0 false false false

Moving on

### Lesson 12
[GO VARABLES WIT INIT](http://tour.golang.org/#12)  

    package main

    import "fmt"

    var i, j int = 1, 2
    var c, python, java = true, false, "no!"

    func main() {
        fmt.Println(i, j, c, python, java)
    }

A var declaration can include initializers, one per variable.

If an initializer is present, the type can be omitted; the variable will take the type of the initializer.

The above would print
    1 2 true false no!

Moving on


### Lesson 13
[GO SHORT VARABLE DECLARATIONS](http://tour.golang.org/#13)  

    package main

    import "fmt"

    func main() {
        var i, j int = 1, 2
        k := 3
        c, python, java := true, false, "no!"

        fmt.Println(i, j, k, c, python, java)
    }

Inside a function, the := short assignment statement can be used in place of a var declaration with implicit type.

Outside a function, every construct begins with a keyword (var, func, and so on) and the := construct is not available.

":=" means that we can throw a var declaration INSIDE a func

REF [Implicit Type](http://en.wikipedia.org/wiki/Type_conversion)

Moving on

### Lesson 14
[GO BASIC TYPES](http://tour.golang.org/#14)  

    package main

    import (
        "fmt"
        "math/cmplx"
    )

    var (
        ToBe   bool       = false
        MaxInt uint64     = 1<<64 - 1
        z      complex128 = cmplx.Sqrt(-5 + 12i)
    )

    func main() {
        const f = "%T(%v)\n"
        fmt.Printf(f, ToBe, ToBe)
        fmt.Printf(f, MaxInt, MaxInt)
        fmt.Printf(f, z, z)
    }

   

    bool

    string

    int  int8  int16  int32  int64
    uint uint8 uint16 uint32 uint64 uintptr

    byte // alias for uint8

    rune // alias for int32
         // represents a Unicode code point

    float32 float64

    complex64 complex128

Moving on

### Lesson 15
[GO TYPE CONVERSION](http://tour.golang.org/#15)  

    package main

    import (
        "fmt"
        "math"
    )

    func main() {
        var x, y int = 3, 4
        var f float64 = math.Sqrt(float64(3*3 + 4*4))
        var z int = int(f)
        fmt.Println(x, y, z)
    }

The expression T(v) converts the value v to the type T.

Some numeric conversions:

    var i int = 42
    var f float64 = float64(i)
    var u uint = uint(f)

Or, put more simply:

    i := 42
    f := float64(i)
    u := uint(f)

Unlike in C, in Go assignment between items of different type requires an explicit conversion. Try removing the float64 or int conversions in the example and see what happens.

Moving on.

### Lesson 16
[GO CONSTANTS](http://tour.golang.org/#16)  

    package main

    import "fmt"

    const Pi = 3.14

    func main() {
        const World = "世界"
        fmt.Println("Hello", World)
        fmt.Println("Happy", Pi, "Day")

        const Truth = true
        fmt.Println("Go rules?", Truth)
    }

Constants are declared like variables, but with the const keyword.
Constants can be character, string, boolean, or numeric values.
Constants cannot be declared using the := syntax.

Constants are by convention Capital cased - 

Moving on

### Lesson 17
[GO NUMERIC CONSTANTS](http://tour.golang.org/#17)  

    package main

    import "fmt"

    const (
        Big   = 1 << 100
        Small = Big >> 99
    )

    func needInt(x int) int { return x*10 + 1 }
    func needFloat(x float64) float64 {
        return x * 0.1
    }

    func main() {
        fmt.Println(needInt(Small))
        fmt.Println(needFloat(Small))
        fmt.Println(needFloat(Big))
        //fmt.Println(needInt(Big))
    }

Numeric constants are high-precision values.
An untyped constant takes the type needed by its context.
Try printing needInt(Big) too.

NOTE: What are high-precision values?

Moving On

### Lesson 18
[GO FOR](http://tour.golang.org/#18)  

    package main

    import "fmt"

    func main() {
        sum := 0
        for i := 0; i < 10; i++ {
            sum += i
        }
        fmt.Println(sum)
    }

Go has only one looping construct, the for loop.

The basic for loop looks as it does in C or Java, except that the ( ) are gone (they are not even optional) and the { } are required.

NOTE: DON'T Bracket for loops

Moving On

### Lesson 19
[GO FOR ++](http://tour.golang.org/#19)  

    package main

    import "fmt"

    func main() {
        sum := 1
        for ; sum < 1000; {
            sum += sum
        }
        fmt.Println(sum)
    }

As in C or Java, you can leave the pre and post statements empty.
NOTE: probably shouldn't use this as this might be hard to debug or differenciate.

Moving On

### Lesson 20
[GO FOR WHILE](http://tour.golang.org/#20)  

    package main

    import "fmt"

    func main() {
        sum := 1
        for sum < 1000 {
            sum += sum
        }
        fmt.Println(sum)
    }

At that point you can drop the semicolons: C's while is spelled for in Go.

NOTE: hmmm, not really got a preference in using this while for looping right now~

Moving On.

### Lesson 21
[GO FOR EVER](http://tour.golang.org/#21)  

    package main

    func main() {
        for {
        }
    }

If you omit the loop condition it loops forever, so an infinite loop is compactly expressed.


Moving on~
END OF PART 2: 