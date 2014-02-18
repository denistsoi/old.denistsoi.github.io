---
layout: post
title: "getting started with golang Part 1"
description: ""
category: 
tags: []
excerpt: 
---
{% include JB/setup %}

If you're just starting with GO - you're in good hands, because the documentation for Go Lang is pretty good compared to other things I've seen.

For starters - head over to [Tour of GO](http://tour.golang.org/)

### Lesson 4  
[GO PACKAGES](http://tour.golang.org/#4)

    package main

    import (
        "fmt"
        "math/rand"
    )

    func main() {
        fmt.Println("My favorite number is", rand.Intn(10))
    }


Every Go Program is made up of packages, and will init the page `main` to begin with.
Within this program, we are using the following packages with import paths `fmt` and `math/rand`.

`fmt` is dealing with out input/out, much like 'stdio' in C or 'stdin' in C++.  
Moving On.


### Lesson 6  
[GO EXPORTED NAMES](http://tour.golang.org/#6)  
    package main

    import (
        "fmt"
        "math"
    )

    func main() {
        fmt.Println(math.Pi)
    }   


It appears that ever importing a package, the dev refer to the package exports if the name begins with a Capital letter. "Foo" is an exported name, as if "FOO". the name "foo" will not be exported.
Comment: "odd - but i'll play along".

```fmt.Println(math.Pi)
will run whereas 
```fmt.Println(math.pi)
will not~

Moving On.

### Lesson 7
[GO FUNCTIONS](http://tour.golang.org/#7)  

    package main

    import "fmt"

    func add(x int, y int) int {
        return x + y
    }

    func main() {
        fmt.Println(add(42, 13))
    }

functions seems pretty straight forward - though we do need to be aware of the var declaration types.

seems we can also refactor `x int, y int` to `x,y int` - 

Moving On.

### Lesson 9
[GO MULTIPLE RESULTS](http://tour.golang.org/#9)  

    package main

    import "fmt"

    func swap(x, y string) (string, string) {
        return y, x
    }

    func main() {
        a, b := swap("hello", "world")
        fmt.Println(a, b)
    }

"A function can return any number of results" - Hmmm - interesting...
I'm not too sure what this means~
    a, b := swap("hello", "world") 
May explain this later in the documentation

Moving On.

### Lesson 10
[GO NAMED RESULTS](http://tour.golang.org/#10)  

    package main

    import "fmt"

    func split(sum int) (x, y int) {
        x = sum * 4/9
        y = sum - x
        return
    }

    func main() {
        fmt.Println(split(40))
    }

As functions can return multple "result params",  they can be names and act just ike variables. 

If the results are named, a return statement without arguments will return teh current values of the results.

So in the above, the return statement will return both x and y where they are equal to their assignment values.

Moving On.

END OF PART 1: 