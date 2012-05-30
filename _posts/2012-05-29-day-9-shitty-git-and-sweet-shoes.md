---
layout: post
title: "Day 9: Shitty Git and Sweet Shoes"
description: ""
category: 
tags: []
---
{% include JB/setup %}

*I'm Jesse Pollak, a rising sophomore at Pomona College outside of Los Angeles. This summer, I'm a hackNY Fellow and technical intern at BuzzFeed. I'm living in Union Square, working in the Flatiron District, gradually finding my way around NYC, and hoping to learn as much as possible (about anything and everything). To assist in that learning process, I've decided to write a blog post every day (I've never been able to last longer than a week, so wish me luck): today is day 9.*

The day started at 7:45am when I woke up (naturally), put my running shoes on, and headed out into the city for my first run. Unfortunately, although unsurprisingly, it was not nearly as enjoyable as I expected. New York is stinky and crowded and, when you're running, those two qualities are really intensified. Running down the street trying to dodge people, while my nose is filled with smells of trash and pee isn't the best way to start the morning, but once I got out to the west side of Manhattan, things got a lot nicer. By the end of the run, the heat had me feeling like crap, but I hoped it would energize me for the day...

At work, I had to correct a bug we introduced in the data retention rates in the morning, then fine tuned the TCP to UDP bridge and dashboard in the afternoon. By the end of the day, everything was working well, my code was almost through review, and my git repositories were in great shape...not. By **far** the worst part of the day was dealing with git: learning a new git workflow has been really hard for me for some reason. I always forget to branch, rebase, and fetch at the right times, so I constantly have to try and retrace my steps to get everything in the right place. This leaves my branches clogged with unnecessary commits and cruft. In the next few days, I really want to nail down the workflow, so I can stop wasting time fixing my mistakes.

My **one big thing learned today** (if you're confused what that means, [see my first post](http://jpollak92.github.com/2012/05/21/day-1-dont-be-afraid-to-ask-questions/)) was the power of writing callbacks into your own javascript functions—especially when manipulating the DOM with jQuery or a similar library. With animations and the like, if you just call one custom function after another, elements will often be in a different place than you think they should be: a bug whose cause can be really hard to track down. Instead, write the second function as a callback to the first. For instance, here's a function I wrote to manipulate the position of graphs on the dashboard:

    function adjustGraphPosition(height, direction) {
    	var graphs = $('.graph');
    	if(direction) {
    		graphs.each(function() {
    			$(this).animate({
    				top: height + $(this).offset().top + 8
    			}, '1000', function() {});
    		});
    	} else {
    		graphs.each(function() {
    			$(this).animate({
    				top: $(this).offset().top - height - 8
    			}, '1000', function() {});
    		});
    	}
    }
    
If I were to call this function and then directly after a saveGraphs() function, to save the graphs to the database, the position of the graphs would be wrong: they are being saved mid-animation (a bug I had today). Instead, write in the callback function:

    function adjustGraphPosition(height, direction, callback) {
    	var graphs = $('.graph');
    	if(direction) {
        ...
    	}
    	(callback && typeof(callback) === "function") && callback();
    }
    
    adjustGraphPosition(100, true, function() { saveGraphs() });
  
Now, it's guaranteed that the saveGraphs() function will run after the graphs are done animating. Callbacks to the rescue!

Here are a few **new and little learnings, tricks and tips**:

* for a shorthand for backing up a file, you can do `mv filename{,.x}`. This will expand to `mv filename filename.x`, neat.
* `isNaN(object)` checks if the object is an NaN
* Don't fuck up Git, it sucks to fix (see above)
* `ifconfig` shows your active/inactive network adapters
* conditional assignment is very convenient: `var x = (a || 1)` or `(callback && typeof(callback) === "function") && callback()`
* to sniff packets, you can do `tcpdump -ni NETWORKADAPTER -s0 -nt`

And, the one **new thing I want to learn and/or accomplish in the next few days (and for the rest of the summer)** is to become more comfortable with uncomfortable situations. To help this goal, I want to try and put myself in **at least 3 uncomfortable situations per day**. I'll write about them here!

Finally, **some fun things**:

* if all else fails, add `&format=json` to an API call. Today, I was using an API that had documentation exclusively on XML (no mention of JSON). On a whim, I added that parameter and (amazingly) it turned to JSON--way, way, better. Do better documentation please NewsCred.
* I met an awesome guy on the elevator today who was shopping designs of shoes based on fruits and vegetables to a shoe company in my building. He showed me designs based on bananas and collar greens: I wish I had pictures!
* Gmail does not count "."s or "+"s in email addresses. So, if you want to register on a site twice, but not use a different email address for the correspondences, use `youremail+123@gmail.com`.
* Supposedly there is an awesome flea market on 75th and Columbus on Sundays...gotta go.
* I can't draw.


