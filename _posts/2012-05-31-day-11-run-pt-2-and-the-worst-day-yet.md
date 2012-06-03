---
layout: post
title: "Day 11: Run pt. 2 and the Worst Day Yet"
description: ""
category: 
tags: []
---
{% include JB/setup %}

*I'm Jesse Pollak, a rising sophomore at Pomona College outside of Los Angeles. This summer, I'm a hackNY Fellow and technical intern at BuzzFeed. I'm living in Union Square, working in the Flatiron District, gradually finding my way around NYC, and hoping to learn as much as possible (about anything and everything). To assist in that learning process, I've decided to write a blog post every day (I've never been able to last longer than a week, so wish me luck): today is day 11.*

Yeah, I said it: worst day yet. Luckily, when the second worst day has been 'great,' the worst isn't that bad. In fact, today was hard, boring, frustrating, and slow, but I still loved it. I'll start from the beginning: left at 8:15am for a run on the East Side, got serious cramps on the way back, and ended up getting to work later than usual. The beginning of work was pretty normal: implementing a feature on the stats dashboard that people had requested. After I was done with that, however, things started to go downhill.

Yesterday, I sat down with my boss and some of the data scientists at BuzzFeed and settled on what my next project would be: I'll be building another data visualization. This sounds straightforward enough, but digging into a database schema, and codebase, that's millions of lines of code in a language I've never coded in (Perl) proved a significant roadblock. Thus, a lot of today was spent setting up my local dev environment with the right data and trying to trace function calls increasingly deeper into the BuzzFeed codebase (finally terminating in machine learning code written in C++). At the end of the day, I felt like I hadn't accomplished much: I'm hoping that tomorrow I'll work with some of the engineers to get a better understanding of how everything works, so I can really tackle the task next week.

There was; however, one fun thing that I got to do today: I started learning d3.js in anticipation of some of the visualizations I would be writing with the data I will (hopefully) have. So, my **one big thing learned today** (if you're confused what that means, [see my first post](http://jpollak92.github.com/2012/05/21/day-1-dont-be-afraid-to-ask-questions/)) was a basic understanding of how d3.js works (and how unbelievably powerful it is). Here's a little demo I made today by following a tutorial on their site:

<div class='d3'> </div>

<script src="http://d3js.org/d3.v2.js"> </script>
<script>
  (function() {
    var t = 1297110663,
    		v = 70,
    		w = 20,
    		h = 80,
    		data = d3.range(29).map(next),
    		x = d3.scale.linear().domain([0, 1]).range([0, w]),
    		y = d3.scale.linear().domain([0, 100]).rangeRound([0, h]);

    setInterval(function() {
    	data.shift();
    	data.push(next());
    	redraw();
    }, 1500);

    var chart = d3.select('.d3').append('svg')
    			.attr('class', 'chart')
    			.attr('width', w * data.length - 1)
    			.attr('height', h);

    chart.selectAll('rect')
    		.data(data)
    	.enter().append('rect')
    		.attr('x', function(d, i) { return x(i) - .5; })
    		.attr('y', function(d) { return h - y(d.value) - .5; })
    		.attr('width', w)
    		.attr('height', function(d) { return y(d.value); });

    chart.append('line')
    	.attr('x1', 0)
    	.attr('x2', w * data.length)
    	.attr('y1', h - .5)
    	.attr('y2', h - .5)
    	.style('stroke', '#000')

    function next() {
    	return {
    		time: ++t,
    		value: v = ~~Math.max(10, Math.min(90, v + 10 * (Math.random() - .5)))
    	}
    }

    function redraw() {
    	var rect = chart.selectAll('rect')
    			.data(data, function(d) { return d.time; });

    	rect.enter().insert('rect', 'line')
    			.attr('x', function(d, i) { return x(i + 1) - .5; })
    			.attr('y', function(d) { return h - y(d.value) - .5; })
    			.attr('width', w)
    			.attr('height', function(d) { return y(d.value); })
    		.transition()
    			.duration(1000)
    			.attr('x', function(d, i) { return x(i) - .5; });

    	rect.transition()
    			.duration(1000)
    			.attr('x', function(d, i) { return x(i) - .5; });

    	rect.exit()
    			.transition()
    				.duration(1000)
    				.attr('x', function(d, i) { return x(i - 1) - .5; })
    				.remove();
    }
  })();
</script>
<style>
  .chart rect {
    font: 10px sans-serif;
    fill: steelblue;
  	stroke: white;
    text-align: right;
    padding: 3px;
    margin: 1px;
    color: white;
  }
</style>

It's not much, but I helped me get an understanding of how powerful d3.js really is: I hope I'll be able to use it in the coming weeks to make some amazing (and beautiful) stuff. As such, my one **new thing I want to learn and/or accomplish in the next few days (and for the rest of the summer)** is to get better at d3.js and build something awesome.

Despite it being a not so great day, I still picked up some **new and little learnings, tricks and tips**:

* `%` is a wildcard in sql
* in bash, you can give long commands short names using `alias` like: `alias shortname= long long long long long long long long long command`
* use your .ssh config file, it's awesome. Nickname a connection like this:

.
    
    Host *hostname* *name you want*
      Hostname *hostname*
      User  *user*
      Port *port*
      
  Then you can call it by going `ssh *name you want*`
  
* In bash, use `>` to pipe output into a file
* To restore a sql database, do `mysql *database* < *backup_file.sql*`

And finally, **some fun things!**

* I've been on a spending spree lately: upgrade to 3gb of data per month AND registered for the free trial of Spotify premium...big spender.
* Accordingly, my headphones came in the mail today. Still [awesome as ever](http://www.amazon.com/Tenqa-Remxd-Bluetooth-Headphones-White/dp/B006LADLLS/ref=sr_1_2?ie=UTF8&m=AXZVDFHSL0GV4&s=generic&qid=1338517564&sr=1-2)
* I cooked my first dinner in the city:

![Fooood](http://distilleryimage7.instagram.com/d0d5a196ab8d11e192e91231381b3d7a_7.jpg)