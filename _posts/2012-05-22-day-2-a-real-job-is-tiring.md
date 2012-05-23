---
layout: post
title: "Day 2: A Real Job is Tiring"
description: ""
category: 
tags: []
---
{% include JB/setup %}

*I'm Jesse Pollak, a rising sophomore at Pomona College outside of Los Angeles. This summer, I'm a hackNY Fellow and technical intern at BuzzFeed. I'm living in Union Square, working in the Flatiron District, gradually finding my way around NYC, and hoping to learn as much as possible (about anything and everything). To assist in that learning process, I've decided to write a blog post every day (I've never been able to last longer than a week, so wish me luck): today is day 2.*

It wasn't the sunny day I was hoping for, but the weather was certainly better than yesterday. The morning started off with me walking 10 blocks in the opposite direction of my office to pick up my NYU ID card (which has one of the worst photos of me ever taken), then 20 blocks back to my desk at BuzzFeed. Once there, I started work on the front end for the real time analytics dashboard I'm building for BuzzFeed. Here's a screenshot of my progress by the end of the day:

![Screenshot](http://f.cl.ly/items/3z3V3h2h293k451d1w3B/Screen%20shot%202012-05-22%20at%2010.44.29%20PM.png)

It's coming along quickly, now I just need to get the real data working and we should be good to go!

After work, I headed uptown for the first time to grab dinner with my cousins at 86th and 5th Ave, then returned home for an early night.

My **one big thing learned** (if you're confused what that means, [see my first post](http://jpollak92.github.com/2012/05/21/day-1-dont-be-afraid-to-ask-questions/) was that **I am extremely lucky to have a job that I seem to love**. It dawned on me mid-afternoon when I checked the clock and saw that it was 12:30; rather than thinking "thank god, time for lunch," I was disappointed because I had less time in the day to work than I expected. I want more time, not less. I look forward to the beginning of my day, not the end. It's awesome—I just hope it holds up.

Here are my **new and little learnings, tricks and tips** (if you haven't picked up on the trend, see my first post again):

* to get the selected option in a select input in javascript, you have to do `selectInput.options[selectInput.selectedIndex].value`. In jQuery, it's `selectedInput.val()`—the joys of jQuery.
* to loop over DOM element in jQuery you can do:

    `$('.elements').each(function(index) {
		blah blah
    });`

* the first time you set up MongoDB on a mac, you have to remember to create your db folder and set the correct permissions:

	`sudo mkdir -p /data/db`  
	`sudo chown 'id -u' /data/db`
	
* inside most traversing functions in jQuery, like `.children()`, you can add selectors, like `.children('img.funny')`
* there **needs** to be better documentation for everything (I know, impossible wish)
* jQuery UI draggable plugin is awesome and easy to use
* Mint **needs** to have weekly (rather than monthly) budgeting

Second to last, the  **new thing I want to learn and/or accomplish in the next few days** is Node.JS more completely. I'm building an app in it and need to get better.

And finally, **some fun things**:

* My standing desk quest continued: **3 out of 8 hours total standing!**
* Edleman's Deli is delicious....reuben.
* I got some restaurant recommendations:
	- Japonika
	- Aki
	- Kefi Greek
* I walked 40+ blocks today

And finally, the best view of the trip so far:

![View](http://f.cl.ly/items/1K1g2h0j0Z1v472g1U3M/photo.JPG)