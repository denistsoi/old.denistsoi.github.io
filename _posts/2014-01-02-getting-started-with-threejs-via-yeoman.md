---
layout: post
title: "Getting started with Threejs via Yeoman"
description: ""
category: 
tags: [Yeoman, Threejs]
excerpt: 
---
{% include JB/setup %}

### Using Yeoman to getting started with Threejs

[Source](https://github.com/timmywil/generator-threejs)

### Getting Started  

There isn't a lot to know if you've followed the previous ['Getting Started with Yeoman' Post](http://denistsoi.github.io/2014/01/01/getting-started-with-yeoman/),
however, if you haven't read that already, I'll include what you need to know below.

``npm install -g yo``

This will install yeoman globally if you haven't already.

``npm install -g generator-threejs``

This is make yeoman install a threejs generator for you.  

Afterwards, go into the folder of your threejs project and

``yo threejs``

You then have the option of running allow AMD into your project.

Note: If you're unfamiliar with AMD, like I am at this current moment, then I implore you to read the [following.](https://github.com/amdjs/amdjs-api/wiki/AMD)

If you just want a stock threejs project, then this should get you going.

Run ``grunt serve`` in your terminal to init a grunt server to view your project in browser.