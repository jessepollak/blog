---
layout: post
title: "Day 10: Mocks and 'Quizma'"
description: ""
category: 
tags: []
---
{% include JB/setup %}

*I'm Jesse Pollak, a rising sophomore at Pomona College outside of Los Angeles. This summer, I'm a hackNY Fellow and technical intern at BuzzFeed. I'm living in Union Square, working in the Flatiron District, gradually finding my way around NYC, and hoping to learn as much as possible (about anything and everything). To assist in that learning process, I've decided to write a blog post every day (I've never been able to last longer than a week, so wish me luck): today is day 10.*

Another early morning, another chance to shy away from my commitments. Getting up is never easy; getting up early to work out for an hour before you head to work for the whole day and know you won't be getting back until 10:30 is nearly impossible. Somehow, I managed to pull myself out of bed, slide on my shoes, and tromp down to the gym. Palladium's gym is beautiful: lovely pool, basketball court, free spin class, nice weight room, snack bar; they've got everything. After an hour of chest exercises, however, the loveliness didn't mean much: my arms were drooping as I dried myself off outside the shower.

Work today was a little frustrating: for the first time, I hit a point where I didn't really know what to do. Luckily, I quickly busied myself with something 'fun': writing unit tests for the TCP to UDP bridge I whipped up earlier this week. Being the first time I'd ever written tests in Node.js, I had to find the right framework, learn the semantics, etc etc. I lost a lot of time doing that. Then came the real problem: how to mock out the UDP socket that was sending the data to the StatsD server.

Here's where my **one big thing learned today** (if you're confused what that means, came in [see my first post](http://jpollak92.github.com/2012/05/21/day-1-dont-be-afraid-to-ask-questions/)): you don't have to use a mocking framework, you can create your own mocks! I used a Node.js module called Horaa to hijack function calls on modules, then mocked up the objects they created and sent back just using a straight up javascript `Object`. Here's the code I'm trying to test:

    var buf = new Buffer(send);
    var client = dgram.createSocket('udp4');
		client.send(buf, 0, buf.length, 8125, 'statsd.buzzfeed.com', 
		function(err, bytes) {
			client.close();
			if(err) {
				console.log("Error sending data: ", err);
				res.send(500);
			} else {
				res.send(200);
			}
		});
		
Pretty much, I create a UDP socket then use it to send a Buffer (encoded string) to the statsD server (port 8125, host 'statsd.buzzfeed.com'). The problem with mocking this code is that buffers cannot be compared one-to-one. So, if I create a buffer with "test", it won't be directly equal to a second buffer created with 'test'. So, it's impossible to say exactly what arguments the `client` is going to receive in the send call. Here is the test code I used to solve the problem:

    dgramHoraa.hijack('createSocket', function() {
			socket = new Object();
			socket.send = 
			  function(buffer, offset, length, port, host, callback) {
  				offset.should.equal(0);
  				length.should.equal(8);
  				port.should.equal(8125);
  				host.should.equal('statsd.buzzfeed.com');
  				callback("Mock error, don't worry!");
  				}
			socket.close = function() {
				return true;
			}
			
As you can see, I hijack the `createSocket` function and create a new `Object()` which I call socket. Then, I just assign new methods to `.send` and `.close`. The send method checks that all of the things I **can check** (not buffer) are equal, then calls the callback function, which closes the socket and sends the correct response. With Horaa, this object is passed back instead of the real socket, the new send and close functions are called, and everything works beautifully. I never knew mocks were this easy!

After work, I headed to Betaworks to listen to the co-founders of [Branch](http://branch.com) (an awesome startup in private beta right now) share their story. I went from being completely dismissive of their project to thinking it has a huge shot of being very successful. HackNY fellows for the win!

With the big learning out of the way, here are my **new and little learnings, tricks and tips**, a lot of them from Branch insights:

* `object.prototype.function` can be used to add values and methods to objects in javascript
* I need to make sure I leave every meeting with **more meetings**
* You get places by making lots of small, uncomfortable, steps
* You're co-founders should be your best friends
* In startups, you should go boring when possible with tech

And, **some fun things!**

* VCs love taking meetings...that doesn't mean anything for your startup though
* A prime quote: "For curing cancer....the product/market fit is already there"
* Justin Schaffer, an big Facebook PM, was supposedly the MVP tech liason of the first hackNY hackathon--he stayed up all night and helped people with problems that had nothing to do with his product at the time
* Betaworks shares it's building with a bunch of super model agencies or something...

10 days down, 60 to go. I'm feeling good, learning a ton, and loving life. NYC is awesome.