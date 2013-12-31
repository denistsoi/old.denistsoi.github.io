---
layout: post
title: "Getting started with gruntjs"
description: ""
category: 
tags: []
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

---  

### Continuing onwards  

Using Yeoman with Angular-Generator [Link](http://www.youtube.com/watch?v=iUQ1fvdO9GY#t=113)  

Install Yeoman globally with  


``$ npm install -g yo``  
``$ npm install -g generator-angular``


Make a new directory of where you want to put your app  


``$ mkdir todo``  
``$ cd todo``  
``$ yo angular`` 


If everything went well, then run  

``$ grunt server``


###Update SUCCESS!  
---

If you'd like to read more about how I got on with using Yeoman with Angular, I write an extension of this post with a relevant link later.

Thanks for reading!

###Footnotes:  
###[Yo-Mobile?](https://github.com/yeoman/generator-mobile)