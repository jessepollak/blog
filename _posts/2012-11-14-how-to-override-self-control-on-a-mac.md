---
layout: post
title: "How to override Self Control on a Mac"
description: ""
category: 
tags: []
---
{% include JB/setup %}

Today, after enabling [Self Control](http://selfcontrolapp.com) for the umpteenth time, it clicked in my head how it blocks the sites on your blacklist. Luckily, despite the fact that I can now override my decision with a couple commands, it still provides an extra layer of procrastination protection.

I figured that it might be useful to post a little tutorial to override [Self Control](http://selfcontrolapp.com) for someone who didn't necessarily know what Terminal was or how to edit their /etc/hosts file. If you're reading this, a friend probably set your timer to 24 hours, so hopefully I'm lending a hand (and not actively ruining your study habits). Bad luck or bad habits, feel free to follow this quick guide to override Self Control.

First, pen the Terminal application, which you can find in the Utilities folder inside of the Applications folder and type (then hit enter):

{% highlight python %}

sudo nano /etc/hosts

{% endhighlight %}

and enter your system account password. At this point, a file will open up that should display something like:

![/etc/hosts]({{ ASSET_PATH }}images/selfcontrol.png)

If you don't see the [Self Control](http://selfcontrolapp.com) chunk, use your arrow keys (your mouse won't work in Terminal) to scroll down. Now, use your arrow keys to move the cursor (that grey thing) down below the section that contains:

{% highlight python linenos %}

# BEGIN SELFCONTROL BLOCK
0.0.0.0 facebook.com
0.0.0.0 www.facebook.com
0.0.0.0 twitter.com
0.0.0.0 www.twitter.com
0.0.0.0 news.ycombinator.com
0.0.0.0 www.news.ycombinator.com
# END SELFCONTROL BLOCK

{% endhighlight %}

With your cursor below this chunk of text, hold down delete and remove it all. Now, hit `ctrl-O`, `enter`, `ctrl-X` and quit Terminal.

The limitations that [Self Control](http://selfcontrolapp.com) was imposing should be removed.

<p class='endnote'>Confused as to what you just did? Run into trouble? Just want to say hi? Tweet at me at <a href='http://twitter.com/jessepollak'>@jessepollak</a></p>.

