---
layout: post
title: "Big Trouble in Little Chinese Language Files"
description: ""
category: 
tags: [Language, Frontend, Web Dev]
excerpt: 
---
{% include JB/setup %}

Today was a bit of stange day - 

<!-- ...I encountered  file and I hope I can outline some scenarios so you too can avoid the eventual faceplant same pitfalls that I almost faceplanted.
 -->

Basically, from GA FEWD and in Frontend, you will want to import custom font files that are either hosted locally or on a CDN like [google fonts](http://www.google.com/fonts).

If you want to include a open font type, you will need to include the `@font face` within your CSS. Thereafter, you'll be able to control what elements you want that font style applied into your webpage.

Below is an example of how you'll go about doing that.

    @font-face
    {
    font-family: myAwesomeFont;  
    src: url(awesomeFont.ttf), local(awesomeFont);  
    }

Then in your stylesheet under your specified class, id or element, you'll need to add this onto your choice of element. (I've used body as the example)

    body
    {
    font-family: myAwesomeFont;
    }

Caveat: Font face is not supported on ie8 and under.

---

####So what's the problem?

Well, the problem was as follows - 
Traditional Chinese was being rendered onto the DOM, along with the Simplified Chinese - so what was the problem?

Whenever I looked at the Mac version of the site, the Simplified Chinese was being rendered with a system font which looked incredibly similar to the desired style that I wanted to render.
However, whenever this was rendered on a Windows Machine on Chrome (running the exact same browser), the Windows system font would actually a very different font style?

So what was actually happening?

I had hypothesized that the Traditional Chinese font file was renderering _SOME_ of the Simplified Chinese, but the curious case was why was it rendering only some and not _ALL_ of the characters?

This lead me onto a deep and dark rabbit hole which would inevitably lead me to some very intereresting caveats about using font types.

As Web Developers, we all know that the openness of the web was not created for font foundries in mind. 
That being said, any font that isn't openly licensed or legally purchased will be liable to some bad times...

![Bad Time](http://cdn.memegenerator.net/instances/500x/44606316.jpg "Bad Time")

####Update

Anyways - that Tangent aside, my colleague Ethan had a quick look around at the most popular only font foundaries about why the font files had specific naming.

There was a peculiar naming scheme of "Simplified on Traditional"...

Which meant...

That for whatever Traditional Chinese character code will be translated into Simplified Chinese via the font file...

###WTF?

