---
layout: post
title: "Selenium, sneakily sterling while still stinking"
description: ""
category: 
tags: []
---
{% include JB/setup %}

*I'm Jesse Pollak, a rising sophomore at [Pomona College](http://pomona.edu). This summer, I'm a [hackNY](http://hackny.org) Fellow and technical intern at [BuzzFeed](http://buzzfeed.com). To assist in my learning process, I've decided to write a blog post every day: today is day 57. You can [follow me on twitter](http://twitter.com/jessepollak) or keep reading my [blog](http://jessepollak.me).*

Even if no one finds this post interesting, that title will still keep me happy—I think it's one of my better moments of the summer.

[Selenium](http://seleniumhq.org/) is a framework that allows you to write code that *automates browsers*. Primarily, it's used for writing automated tests of front end functionality on web applications—or at least that's what I've been doing with it. The functionality of Selenium is *very, very cool*; however, just like with most things, it's never as easy as it seems. While the commands are natural language ("click", "wait", "open"), they inevitability never work as expected. This means that often times things *seem* like they should be working, but they just aren't—and you don't really know what to do. For this reason, Selenium often has a reputation for "the worst" thing to be working on.

Over the last few days, I've been having some Selenium struggles of my own while writing tests for a consumer facing feature I'm writing for BuzzFeed. Today, in the morning, those frustrations escalated as I hit points where I thought to myself: "what the fuck, this should be working." In the afternoon, however, things started clicking and I began to understand why Selenium can be very valuable. I thought I'd share a nice little example where Selenium actually saved the day.

Consider the following snippet of code:

{% highlight javascript linenos %}	  
ajax.request('<request location>', {
	method: 'get',
	parameters: {},
	onSuccess: function(response) {
	  var authentications = JSON.parse(response.responseText);
	  wrapper.down('loading-gif').hide();
	  //insert current authentications
	  authentications.each(function(a) {
	    //insert into a table in the DOM
	  });
	  //add handlers to newly added authentications
	  add_new_prompts([assign_new_handlers, assign_new_social_handlers]);
	}
}
{% endhighlight %}
	  
Basically, I do an AJAX request to load some data, hide the loading GIF onSuccess, insert the formatted data into the DOM, then, in the last line, do some more manipulation and assign handlers to the new DOM that I just added in the each loop. Looking at the code, it seems to make sense: I add the new stuff to the DOM and then assign the handlers—pretty standard stuff. And, in the hand testing I did, everything worked great. The DOM got manipulated, the handlers worked, sunshine shown and birds sang.

This morning, however, I was struggling mightily with some Selenium tests and I *could not figure out what was going on*. These are the basics of the Selenium steps:

1. Wait for 'loading-gif' to *not* be visible
2. Wait for all the new authentications DOM material to be added
3. Click button that uses the handlers assigned in the last line

And, shocker, something was going wrong: rather than doing the functionality I wanted, the button I was clicking, which was an `input`, was posting a form. Hmmmm. I thought: "if it works for me when I do it by hand, why isn't it working for Selenium! This sucks!"

Eventually, however, I realized the (pretty obvious) mistake I was making—all thanks to Selenium. Primarily, I was *assuming* that the event handlers were being attached in a very speedy manner. And, they were—probably on the order of ~100ms, barely long enough for a human to see, and definitely not long enough to matter when a human has to move a mouse to click the button the handlers are being attached to.

For Selenium, however, it's a little different: since it's just javascript, it **can** "move and click the mouse" in less than 100ms. This meant it was clicking the input *before* my handlers were attached: triggering the default functionality of posting a form.

To be honest, this is a pretty stupid assumption to make in my code; however, it's also pretty easy to dismiss or overlook. Without Selenium, I can safely say that I never would have caught it. And, while my computer may be fast enough to assign those handlers before I notice, that may not be the case on a slower computer: potentially ruining the user experience for a BuzzFeed reader out there. The fix:

{% highlight javascript linenos %}

//hide the table that the new data will be inserted into
wrapper.down('table').hide(); 
ajax.request('/buzzfeed/super_share', {
	method: 'get',
	parameters: {},
	onSuccess: function(response) {
	  var authentications = JSON.parse(response.responseText);
	  //insert current authentications
	  authentications.each(function(a) {
	    //insert into hidden table in the DOM
	  });
	  //assign handlers BEFORE I hid the loading GIF
	  add_new_prompts([ss.assign_new_handlers, ss.assign_new_social_handlers]); 
	  wrapper.down('loading-gif').hide(); //hide the loading GIF
	  wrapper.down('table').show(); //show the table
	}
}

{% endhighlight %}
			
Now, my Selenium steps work because all the events are attached *before* the 'loading-gif' is hidden. Success!

Selenium can be a huge pain, but lessons like this just show how valuable automated testing can be. In essence: **Selenium is sneakily sterling, but still stinks sometimes**.