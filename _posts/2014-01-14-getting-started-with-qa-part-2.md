---
layout: post
title: "getting started with qa part 2"
description: ""
category: 
tags: [QA]
excerpt: 
---
{% include JB/setup %}

One of the things with getting started with qa is basically the fallacy of most QA articles out there.

QA as a field when comparing it to software development as a whole is an additive process, which helps aid in the develop cycle. However, I believe that adding the QA process as a formal process AFTER the development cycle is complete only hinders both the development cycle and the learning experience of a junior developer.

The thing that I have found as a junior web developer as well as my short time as a QA, is that having the mindset of a QA actually _HELPS_ me as a developer.

"Why" you ask?

The first thing to keep in mind is that as a QA, my job was to address not only the clients issues with respect to a piece of software... but to accurately and effectively communicate the problems to the software development team.

Effective Communication is by far THE MOST underrated skill that a developer can gain within their career. 

If you are a QA and can use the same language and process of breaking down a problem/bug into it's constituent parts, YOU are increasing the effectiveness of the team at solving problems.

Not only does communicating well with your team help them in solving the problem, but having the language to actively find out WHERE the problem lies within the debugging tools saves an incredible amount of time for YOUR team to waste as minimal amount of time searching for the problem.

The biggest problem with bugtracking is reproducing the EXACT conditions of the bugs existance. 

That might sound like a big pile of BS, but hear me out.

If a user/tester does NOT effectively communicate ALL ESSENTIAL aspects of their testing environment, the amount of time WASTED increases exponentially with every piece of information that was omitted.

Example: Web Development.

1. What Browser is the tester using (and limiting to Brand does not help) - 
  As a QA, I want to know EVERYTHING! - the OS, the Version, what Time this was run, what PAGE... Even What BRAND of PC.
2. What did you DO to get to that bug? 
  I want to know EVERYTHING that YOU did so I don't waste time "TRYING" to replicate the damn bug.
3. Testers should focus ONLY on the ONE ISSUE.
  I can't count the number of times where testers will just whine about how "everything is broken"... 
  Look, I don't get paid to listen to your complaints, I ONLY get paid to find out the bugs and convey that to my team. I don't want to hear about anything about the bad day you're having, that's just not being professional.

Anyways - Rant Over...

Here's a free quick tools you should use when you are doing some QA.

MAC OS X Tools
1. QuickTime Movie for Video Screen Capture 
2. CMD + SHIFT + 4 (to save screen as picture which is usually saved onto your desktop)

Windows Tools
1. CamStudio (Video Capture, Pretty decent for Open Source)
2. FRAPS (Save Screen without using PrntScreen and Paint)

Takeaway Points:
* Be very explicit in your description/outline of the problem. It helps if you provide a video to SHOW devs how the event occurred, and it helps capturing small bugs that you didn't notice the first time round.
* Be patient with your testers, they generally won't know how to express the problem, so if you can train them before hand, that'd be an ideal situation...
Otherwise, try to train them during the testing process.
* Be bold in trying to 'BREAK' the application as hard as humanly possible. 
  Alot of the times, the user won't know how to test the application, so if you are testing out UI interactions, click on a button a thousand times, refresh the page, type stupid shit in the input and repeat. You never know what sort of unexpected behaviour you might produce unless you're bold enough to WANT to break the app.

Anyways - Speak soon
D