---
layout: post
title: "Day 23: A Regular Day at the Office"
description: ""
category: 
tags: []
---
{% include JB/setup %}

*I'm Jesse Pollak, a rising sophomore at [Pomona College](http://pomona.edu). This summer, I'm a [hackNY](http://hackny.org) Fellow and technical intern at [BuzzFeed](http://buzzfeed.com). To assist in my learning process, I've decided to write a blog post every day: today is day 23. You can [follow me on twitter](http://twitter.com/jessepollak) or keep reading my [blog](http://jessepollak.me)*

When I imagine what my life will be like 20 years down the road, it looks a lot like my day today. No, I don't plan on being an intern at BuzzFeed (hopefully, I will have progressed a little!), but the structure of today felt like something I could get used to.

On my way to work, the **one big thing I learned today** (if you're confused what that means, [see my first post](http://jpollak92.github.com/2012/05/21/day-1-dont-be-afraid-to-ask-questions/)) started to form: today, I realized that I won't be able to finish everything in a short amount of time. In fact, I'll probably be able to finish very little in a short period of time. I think the thought that I could *always* finsh something *quicker* is part of why I've been having so much self doubt lately. Things take time, but often when I'm reading what other people have accomplished, it's hard to understand how much effort they invested behind the scenes. With increasingly hard development projects, I'm starting to see that coding time should be measured in days, weeks, and months, rather than hours if it's a project of any importance. Yes, there will be some exceptions, but for the most part, writing code is a very time consuming process.

Back to my first thought: today was a day with many very distinct parts. All in all, I had a very serious conversation, made a stupid mistake, learned a new skill, spoke to important people, solved a problem that had been blocking me, attended a fun social event, and relaxed with old friends (and family). Like I said, if I can replicate that same basic structure for the next 20 years, I'll be a very happy person.

As usual, here are some small **new and little learnings, tricks and tips** from the day:

* use `for $k (keys %$hash)` to iterate over the keys in a hash, not `for $k ($%hash)`.
* you can pipe from bash directly into STDIN in perl
* STDIN buffers and blocks, to have asynchronous I/O in Perl use IO::Select->new(\*INPUT)
* Follow "Joel's Test" when you're considering a tech job
