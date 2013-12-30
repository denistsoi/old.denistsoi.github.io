---
layout: post
title: "getting started with gruntjs"
description: ""
category: 
tags: [Grunt]
excerpt: 
---
{% include JB/setup %}

#### Referencing Article

####[Up and Running with GruntJS](http://coding.smashingmagazine.com/2013/10/29/get-up-running-grunt/)  
  


#### GruntJS Primer

    Built on top of Node.js, Grunt is a task-based command-line tool that speeds up workflows by reducing the effort required to prepare assets for production.  
    It does this by wrapping up jobs into tasks that are compiled automatically as you go along. Basically, you can use Grunt on most tasks that you consider to be grunt work and would normally have to manually configure and run yourself.

Simply put - it helps when you're doing commands like  
    sass --watch main.sass:main.css  
or  
    coffee --compile --watch main.coffee:main.js  
or even  
    python -h SimpleHTTPServer  

and depending on what you put in your grunt file...  
... replace them all with  
`grunt server`


---
Let's get started!

Follow the repo [here](https://github.com/denistsoi/port-js)

---