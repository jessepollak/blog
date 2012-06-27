---
layout: post
title: "Choosing the right technologies for a hackathon"
description: ""
category: 
tags: []
---
{% include JB/setup %}

*I'm Jesse Pollak, a rising sophomore at [Pomona College](http://pomona.edu). This summer, I'm a [hackNY](http://hackny.org) Fellow and technical intern at [BuzzFeed](http://buzzfeed.com). To assist in my learning process, I've decided to write a blog post every day: today is day 36. You can [follow me on twitter](http://twitter.com/jessepollak) or keep reading my [blog](http://jessepollak.me).*

Today, I was going to discuss the general lessons I learned from winning (becoming a finalist, going to SV to pitch) at AngelHack. I just came back from a hackNY lecture with [Peter Bell](https://twitter.com/#!/PeterBell), however, and his discussion encouraged me to write on a more specific lesson.

# Choosing the right technologies for a hackathon

Yesterday, I, along with [Cheryl](http://twitter.com/grungerabbit), [Conway](http://twitter.com/conwayanderson), [Brennen](http://twitter.com/brennenbyrne), and [Jordan](http://twitter.com/thetabyte) were chosen as finalists for Angelhack with our idea, [Mentor.im](http://mentor.im). Basically, this means that after a full 24 hours of straight coding, the judges decided that we should be one of the six teams from NYC to be flown out to Silicon Valley to pitch investors for a chance to win $170,000 in funding. To say the least, it was a crazy weekend—and a result that I never would have expected.

Today, Peter came and talked about how to choose the right technologies for your startup. After dealing with many of the issues he discussed, I thought it was too perfect a juxtaposition to not write on.

# It depends.

That was one of Peter's biggest points about choosing the right technology for a startup. I think a hackathon is a perfect demonstration of this mantra. Yes, I would love to build with the latest (and coolest) technologies, but when you have 24 hours to build a product from scratch, a huge community and easy prototyping is a must. We went with Rails.

# Know your team.

On the [Mentor.im](http://mentor.im) team, we had 2 developers who knew Ruby well and 1 who knew Python. If it had been 2-1 Python, we probably would have gone with Python. The more people you have that are comfortable with a platform, the more successful you will be in development.

# Don't let a technology block you.

You're going to get stuck at some point. The key is knowing when to make a switch. If a technology is actively preventing you from reaching a goal, then it probably isn't the right for the tool. Get comfortable with quickly evaluating situations and weighing whether a change needs to be made. 

At AngelHack, we originally went with the Singly API for authentication. It's a great idea, and a great API, but it is a young one. After writing all of our authentication code, we were unfortunate enough to hit a bug in their API. The first time a user logged in, they passed back an invalid JSON hash, which caused a 500 error on our side. After that, however, everything worked perfectly. We only had 5 "first log ins," since once you authenticated with their website through one site, you authenticated for every site, so it was nearly impossible to debug. Unsurprisingly, we pushed live and instantly started getting 500 errors. I tried to hack together a solution, but it only made the problem worse. This left us trying to fix a live bug as time ticked down—a terrible problem.

Earlier, I'd almost switched our authentication system, but instead decided that the bug "would fix itself."  After the hackathon ended, I completely rewrote the authentication code (which didn't take that long) and now everything is working perfectly! Had I switched earlier, this problem could have been avoided with little time lost.

# The theory of constraints.

Our biggest constraint was time. We used technologies that had been used millions of times before to create similar products. Had our constraint been hiring, we would have used technologies that drew creative and intelligent developers. Find the biggest constraint on what you can do and base your technologies around how to solve that issue.

# Trust your team.

I mentioned above that you should know your team, but that means little if you can't trust them. There will always be thinks you don't know that others do. In that situation, you may have to defer to what a teammate thinks is best—if they are smart, and insistent, they will most likely be right. Catch up as quickly as possible.

I'll have more general thoughts tomorrow, but for now, I need to catch up on sleep. Check out [Mentor.im](http://mentor.im) and follow me [on Twitter](http://twitter.com/jessepollak) if you want the latest updates.

