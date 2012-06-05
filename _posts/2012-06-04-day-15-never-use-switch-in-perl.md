---
layout: post
title: "Day 15: Never Use Switch in Perl"
description: ""
category: 
tags: []
---
{% include JB/setup %}

*I'm Jesse Pollak, a rising sophomore at Pomona College outside of Los Angeles. This summer, I'm a hackNY Fellow and technical intern at BuzzFeed. I'm living in Union Square, working in the Flatiron District, gradually finding my way around NYC, and hoping to learn as much as possible (about anything and everything). To assist in that learning process, I've decided to write a blog post every day (I've never been able to last longer than a week, so wish me luck): today is day 15.*

Learning a new language is never easy: new syntax, new constructs, features that you think should work, but don't, etc etc. Today, my mind was torn to bits by a simple construct that wouldn't compile, check it out:

      if ($total_search == 0 && $total_social == 0) {
    		$ratio = 0;
    	} else {
    	  if ($total_social >= $total_search) {
    			if ($total_search == 0) {
    				$ratio = 1;
    			} else {
    				$ratio = 1 - ($total_social / $total_search);
  				}
    	} else {
    			if ($total_social == 0) {
    				$ratio = -1;
    			} else {
  					$ratio = ($total_search / $total_social) - 1;
  				}
  		  }
   	  }
    	
I spent 2 hours today writing, and rewriting that piece of code, trying to figure out what could possibly be wrong with it. In the end, there was nothing wrong with it: the `switch` statement in Perl, a piece of code I used earlier, is just unreliable (who would have guessed), but there's nothing about the unreliability in the Perl documentation. Luckily I stumbled upon [this](http://www.perlmonks.org/?node_id=784840). Lesson learned: never use the switch in Perl.

Enough with my whining, and onto the better parts of the day. I started with a long run in the rain—the perfect thing to erase the feelings of grogginess from the shortest night of sleep I've had all summer (thanks laundry). After a warm, pitch black shower, I trekked through the rain to the office and settled into work for the day. As I mentioned earlier, I'm working on a pretty cool data visualization for BuzzFeed using d3.js. Today, I had the chance to sit down with the data team to discuss the idea...and a little more. After we were done talking about what I was working on, I got to listen to them examine the stats from BuzzFeed over the last few months. It was an amazing experience.

Accordingly, my **one big thing learned today** (if you're confused what that means, [see my first post](http://jpollak92.github.com/2012/05/21/day-1-dont-be-afraid-to-ask-questions/)) was that with any website, you should **always** track data on performance and user interaction. In the meeting, just by looking at usage stats for different parts of the site, we were able to find bugs, points in the site where people lost interest, and tracking problems. Without these insights, these problems could go unnoticed forever. 

As I mentioned above, I'm working in d3.js to do this visualization, so the one **new thing I want to learn and/or accomplish in the next few days (and for the rest of the summer)** is create a visualization with multiple, animated, pie graphs. Right now, I'm having trouble understanding how to properly nest and manipulate the data I'm binding, but I'm hoping I'll be able to figure it out tomorrow.

After work, I walked to 16th and 5th Ave to enjoy our biweekly hackNY lecture series—this time, Jonah Peretti, the founder of BuzzFeed (!), was talking. To say the least, he is one of the smartest people I've ever heard talk. In his work, he has demonstrated again and again that he can see, and analyze, the trends in our world: whether it be capitalizing on the "bored at work network" in the early internet era, the transition from portal to search providing the majority of traffic, or the jump to social as the new connective tissue of the web, Jonah seems to be able to be there—before it happens. Plus, his ability to articulate this understanding is phenomenal. The conversation was off the record, so I can't share specifics, but he also is a genuinely hilarious person who can really capture the attention of the audience. It was a pleasure listening to him and I hope I'll be able to get to know him better in the coming weeks—I think I could learn a whole lot from his experience and knowledge.

As with every post, here are some **new and little learnings, tricks and tips**:

* the 3D web inspector in Firefox is **absolutely amazing**—everyone should check it out ASAP.
* never use `switch` in Perl (see above -_-)
* with technology, no academics understand the latest trends, so you can teach however you want
* talk **grand** visions to investors——they are looking for huge returns, not just big ones
* raise a round from different investors concurrently to peer pressure investors into committing (like an 8th grade swim party..?)
* NYC needs a few big, independent companies before it can really compare to SV

And some **fun things**:

* [this](http://www.shey.net/niked.html)
* and [this](http://blogdex.net/)...is so sad, oh blogdex, you could have been great
* and [this](http://www.rejectionline.com/)
* and [this](http://www.blackpeopleloveus.com/)

Monday's over, the real week begins.