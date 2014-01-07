---
layout: post
title: "Getting started with QA GUI testing"
description: ""
category: 
tags: []
excerpt: 
---
{% include JB/setup %}

So how do you Automate GUI testing for web applications?

There's an interesting site called [csste.st](http://csste.st/tools/) which is a good source to find more some directions for some CSS Testing tools, however, I'd like to expand this post to include some others.

- We're not talking about Unit Testing here, but about consistently testing and accurately recording the the user flow of web appications, there isn't a great deal of tools available to the Dev...

However, it's a great opportunity to outline a few tools that _CAN_ help to this regard.

[Defacto: "BrowserStack"](http://www.browserstack.com) isn't great if you're trying to hustle, but incredibly powerful if you're able to fork $20 a month. That basic plan doesn't give you all the bells and whistles, but it will give you enough to get pretty far on your Frontend Dev.

[Pricey Alternative: "Mogotest"](http://cssregressiontesting.com/) is a prety interesting site that is trying to compete against BrowserStack, though the plans are pretty expensive.

[Soasta]()

[iMacros]()

---
### #Tools
---

[CSSCritic](http://cburgmer.github.io/csscritic/) is incredibly lightweight and I'd only recommend it for a quick comparison during your dev cycle. It is basically a screen capture plugin to compare two versions of a site which will highlight elements which are out of alignment compared to the original picture.

[Lightweight OpenSource Alt: "PhantomCSS"](https://github.com/Huddle/PhantomCSS) is an alternative to CSSCritic which offers a little more

[Hardy.io](http://hardy.io/) is the big brother to GhostStory

[BBC News Wraith](https://github.com/BBC-News/wraith) is incredibly impressive. Running on Ruby, this uses a `rake` task to run automated screen capture tests which are saved on the local directory.
  I particularly like how you can run the rake task to pull the requested web pages and then save a comparision of two pages as a highlighted image within a gallery context. 
  Another thing I particularly like is how you can specify the screen sizes of the pages that you want the screen shots to be captured.

[Watir](https://github.com/watir/watir) 
[Official Blog site for Watir](http://watir.com/)

---
### #Automated Recorders
---

[Selenium](http://docs.seleniumhq.org/) is a Firebox plugin which allows the user to run browser automation tests. You can program on a plethora of programming languages though I do dislike the fact that you are required to have firefox as a prerequesite.  
  - [Getting Started on Selenium](http://darrellgrainger.blogspot.hk/2010/02/selenium-101.html) 
  - [More in-depth Selenium](http://refcardz.dzone.com/refcardz/getting-started-selenium)  
  - [like Youtube Tutorials?](http://www.youtube.com/watch?v=gsHyDIyA3dg)  
  I like how you can export to Python or Ruby via Web Driver, but I'm a little disappointed that you can't import back into Selenium IDE after you've exported out.  
  - [Selenium-WebDriver](https://npmjs.org/package/selenium-webdriver)

[Sikuli](http://www.sikuli.org/) is a python based IDE for automated testing. 
I tried to use this during my brokerage days to automate financial reporting, but the only caveat is that Sikuli doesn't play nicely when you have buttons that are incredibly small within properietary software.
  There hasn't been much development for a while, which leads me to consider other alternatives
  - [Node-Sikuli](https://github.com/daizoru/node-sikuli) Here is Sikuli to be used for node.


---
### #CLI tools
---

[node-webshot](https://github.com/brenden/node-webshot)
[CasperJS](http://docs.casperjs.org/en/latest/quickstart.html)


---

### #Takeaways

There's some underlying similarities between the different tools currently available. The most common tools that continue to pop up are Selenium Webdriver and PhantomJS.  
Why do you need the Webdriver?  
Why do you need PhantomJs/CasperJS?


---

### #Tips and Tricks for Q&A
- Invalid HTML
- Form Validation
- Content Wrapping
- Tolerance Levels against Design 
- Optimize for one browser type and fix inconsistencies for others?
- Dynamically Generated Content?



---

### #Future Post Ideas

- Browser Stack API?
- What is Web Driver
- Indepth Look at Hardy.io