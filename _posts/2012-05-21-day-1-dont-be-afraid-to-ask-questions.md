---
layout: post
title: "Day 1: Don't Be Afraid to Ask Questions"
description: ""
category: 
tags: []
---
{% include JB/setup %}

Before I get started with my daily post, I'll do a brief introduction to who I am and what I'm doing this summer (for future reference). I'm Jesse Pollak, a rising sophomore at Pomona College outside of Los Angeles. This summer, I'm a hackNY Fellow and will be a technical intern at BuzzFeed. I'm living in Union Square, working in the Flatiron District, gradually finding my way around NYC, and hoping to learn as much as possible (about anything and everything). To assist in that learning process, I've decided to write a blog post every day (I've never been able to last longer than a week, so wish me luck). I don't know exactly what the format of these posts will be, but I'm going to start with a simple structure: 

1. **a brief summary of the daily activities**

2. **one or two big (meaningful, insightful, important) things learned**

3. **a variety of new and little (coding, working, life, food, NYC) learnings, tricks and tips**

4. **one or two new things I want to learn and/or accomplish in the next few days**
  
5. **some fun things** 

  
And so it begins!
  
  
As I mentioned earlier, today was day #1 (well actually I moved in yesterday, but work started today). Unsurprisingly, the weather did not cooperate; thus, my first really hard decision arose: to buy or not to buy an umbrella. I decided not to...for exactly one block. After my pants and shoes were soaked through after 100 yards, I sheepishly ducked into a pharmacy and dropped the $10 for the umbrella. The walk to work in squishy shoes was unenjoyable, but no one seemed to care at the office. At work, I got a new MacBook Pro for the summer, met the Dev team, learned that I would start off working on a real time analytics dashboard, and pushed my first commit! After work, I headed to Little Italy for the hackNY welcome dinner at a tiny italian restaurant (which we filled completely).
  
Since it was my first day, my **one big thing learned** came pretty early on: **never be embarrassed to ask questions**. To say the least, I was completely lost once I started to dig into the Perl codebase (having never used Perl before), so it was no surprise that I had to ask the devs around me a few simple syntax questions. Not going to lie, I was (and still am) pretty scared to ask: I didn't want to seem dull...BUT, everyone was more than eager to help me solve my problems. In fact, by asking these questions I managed to find TWO BUGS in my first day: that felt awesome. It just goes to show, even if I feel stupid, I still need to ask those questions.

Throughout the day, I picked up a bunch of **new and little learnings, tricks and tips**, so here they are:

* `ctrl-Z` actually doesn't quit a process; it pauses the process and it can restarted in the foreground with `fg` or the background with `bg`
* the `-s` option to `grep` suppresses annoying errors like Permission Denied on file searches
* the Perl `bless $self, $class` method is used to indicate that a method instantiates an object
* the `/opt` folder should contain all the things that are not in the default installation
* you can auto refresh a image by using setInterval to change the `img` tags `src` attribute to the same thing
* to add an event to a DOM element you use syntax like: `select.onchange = function() { return true };`

Second to last, the two **new things I want to learn and/or accomplish in the next few days** is learn how to sniff TCP/IP packets on the command line and how to use a GUI text editor (TextMate) to edit files on a remote server. If you have any tips or suggestions, I'd love to hear them in the comments! 

And finally, **some fun things**:

* I've decided to work half of each day at a standing desk! We'll see how long I last..
* I found some good quotes in the source code comments:
	- "lets track some stats, shall we?"
	- "get parents for da index flows!"
* I got to (kind of) meet moot (the guy who founded 4chan) at dinner. He's a big mentor for hackNY—awesome.

Overall, it was a terrific first day.
