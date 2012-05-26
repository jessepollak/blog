---
layout: post
title: "Day 5: Boring Bugs"
description: ""
category: 
tags: []
---
{% include JB/setup %}

*I'm Jesse Pollak, a rising sophomore at Pomona College outside of Los Angeles. This summer, I'm a hackNY Fellow and technical intern at BuzzFeed. I'm living in Union Square, working in the Flatiron District, gradually finding my way around NYC, and hoping to learn as much as possible (about anything and everything). To assist in that learning process, I've decided to write a blog post every day (I've never been able to last longer than a week, so wish me luck): today is day 5.*

Today's a short post for two reasons: (1) nothing really interesting happened today (my notebook was pretty much empty at the end of the day) and (2) it's my first friday in NYC. I'm getting into the flow at work; time passes quickly, I tackle tasks and move on to others, and I'm finally starting to feel like part of the team. Today, I finished up V2.0 of the real time analytics dashboard; now it has live graph previews, graph editing, auto saving, and some nice UX things that were definitely necessary. After I thought I was in a good place with that, I started working on a part of the backend for it. Right now, the analytics backend uses a protocol called UDP to send stats to the server, which processes them. Unfortunately, client side code (i.e. javascript on the front end) cannot send data using UDP, so we have to create a bridge for it. I'm working to create a server that accepts POST requests from client side javascript, processes the data, then uses UDP to send the info to the analytics server. Pretty cool stuff—and I'm learning a lot about UDP, sockets, and servers.

My **one big thing learned** (if you're confused what that means, [see my first post](http://jpollak92.github.com/2012/05/21/day-1-dont-be-afraid-to-ask-questions/)) was how UPD works and what the difference is between it and TCP/IP.

Here are my (brief) **new and little learnings, tricks and tips**:

* `.keyup` can be used to check key presses and 27 is the 'esc' key

And, the one **new thing I want to learn and/or accomplish in the next few days** is avoid burnout. It's been a an awesome, but long week and I'm having tons of fun, but I can see how I might burn out from coding for 10 hours a day. This weekend, I want to get outside, socialize, meet people, and do things a *normal* college kid in NYC might do. Hopefully some good stories for this blog will come of it.

Finally, **a fun thing** from my office:

![Stop Tweeting Boring Shit](http://distilleryimage10.instagram.com/b425ca3aa6bf11e1aebc1231381b647a_7.jpg)