---
layout: post
title: "Getting started with gruntjs"
description: ""
category: 
tags: [Grunt, Yeoman, npm ,sudo]
excerpt: 
---
{% include JB/setup %}

#### Referencing Article

####[Up and Running with GruntJS](http://coding.smashingmagazine.com/2013/10/29/get-up-running-grunt/)  
  
  
  
#### GruntJS Primer
  
    Built on top of Node.js, Grunt is a task-based command-line tool that speeds up workflows by reducing the effort required to prepare assets for production.  
    It does this by wrapping up jobs into tasks that are compiled automatically as you go along. Basically, you can use Grunt on most tasks that you consider to be grunt work and would normally have to manually configure and run yourself.
  
Simply put - it helps when you're doing commands like  

``$ sass --watch main.sass:main.css``  

or  

``$ coffee --compile --watch main.coffee:main.js``
    
or even  

``$ python -h SimpleHTTPServer``
  
However, depending on your Gruntfile, you could just... 

``$ grunt server``

---

##Ok Let's get started... Follow the repo [here](https://github.com/denistsoi/port-js)
Update: 20:00 30-12-2013

OMG, This was a complete pain in the ass.
Ok one of the MOST FRUSTRATING thing you should be aware about is if you have previously had node/npm install, you may need to use the command in your terminal.  
    
``$ sudo npm cache clean``

Why?  
Well, apparently, if you don't clean/clear your cache, some dependancies will give you some errors like...  


``npm ERR! cb() never called!``  
``npm ERR! not ok code 0 ``
  

I ended up using the yeoman generator, which I will outline below after I've worked tried Yeoman with Angular.  
if you are using terminal and keep having the password prompting then the following seems to help  


``$ sudo chown -R `whoami` ~/.npm ``  
``$ sudo chown -R `whoami` /usr/local/lib/node_modules``


There's another command, which I will update at a later date which also seems to the same thing.  

Update - Here is the terminal command to allow global installation via npm

``sudo chown -R $USER /usr/local``

[source](http://foohack.com/2010/08/intro-to-npm/)

---  

I got pretty fed up with trying to generate a stand alone grunt project and ended up with using yeoman - which is further detailed in the following post  
[relevant post](http://denistsoi.github.io/2014/01/01/getting-started-with-yeoman/)