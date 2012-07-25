---
layout: post
title: "Creating awesome graphs with Rickshaw"
description: ""
category: 
tags: []
---
{% include JB/setup %}

*I'm Jesse Pollak, a rising sophomore at [Pomona College](http://pomona.edu). This summer, I'm a [hackNY](http://hackny.org) Fellow and technical intern at [BuzzFeed](http://buzzfeed.com). To assist in my learning process, I've decided to write a blog post every day: today is day 62. You can [follow me on twitter](http://twitter.com/jessepollak) or keep reading my [blog](http://jessepollak.me).*

Earlier this summer, I was tasked with building some data visualizations and network monitoring tools for BuzzFeed. Wanting to learn something new, I decided to pick up the d3.js libray, which allows you to create beautiful Data Driven Documents. While d3.js is a javascript library, unlike most other libraries, d3.js actually involves writing your code using a different paradigm. Everything is centered around data, which you "bind" to DOM elements. At first, this was pretty confusing, but by the end of my project I felt pretty comfortable with the structure. And, by the end, I had built a few apps that displayed data in a way which I thought was beautiful and interactive. 

A couple days ago, a library built *on top* of d3.js came to my attention: [Rickshaw](http://code.shutterstock.com/rickshaw/). After messing around with it for a few days, I'm here to say that it is by far the best bang for your buck in terms of ease of use and beauty for open source javascript graphing solutions. I thought I'd share one of the little projects I built using it and show the code.

BuzzFeed is lucky enough to have <a href='http://en.wikipedia.org/wiki/Ben_Smith_(journalist)'>Ben Smith</a> as it's editor-in-chief and, at the beginning of my internship, I was lucky enough to get a chance to talk one on one with him. Unsurprisingly, we started talking politics and our conversation turned to BuzzFeed's role in the political news scene. Five minutes into our conversation, he gestured for me to come check out his computer and he went [http://memeorandum.com/lb](http://memeorandum.com/lb). For those of you that don't know, [Memeorandum](http://memeorandum.com) is a political news aggregator. The link he was showing me, their Leaderboard, is a ranking of the news sites that provide the most content to their aggregator—with BuzzFeed in the top ten. It was awesome to see BuzzFeed doing so well, but I was disappointed that their wasn't a better way to *see the trend of how BuzzFeed was doing*. The leaderboard got updated daily, but there was no history and no graph of the ranking over time.

The evening, about a month ago, I sat down and wrote a script that would scrape the leaderboard each day and store the ranking in the database. Yesterday, I decided I finally had enough data for it to be cool and sat down with Rickshaw to make the data come alive.

The backend of the app is simple: Sinatra hitting a MongoDB hosted on MongoHQ. If you hit `/data.json`, you'll see what I get from the database: an array of objects in the form `{name: 'News Outlet Name', data: [{x: *time*, y: *percentage of aggregation*}, {x: ,y: }, ...]}`. Now, with Rickshaw I could turn that raw data into something beautiful—in 50 lines of easy to read (and write) code.

    var palette = new Rickshaw.Color.Palette(),
        series = []
    $.get('names.json', function(d) {
      d.forEach(function(s) {
        series.push({
          name: s,
          color: palette.color(s)
        });
      });
      var ajaxGraph = new Rickshaw.Graph.Ajax( {
      	element: document.getElementById("graph"),
      	width: 800,
      	height: 500,
      	renderer: 'line',
      	dataURL: 'data.json',
      	series: series,
      	onData: function(d) {
      	  Rickshaw.Series.zeroFill(d);
      	  return d;
      	},
      	onComplete: function(transport) {
      	  var graph = transport.graph;
      	  var detail = new Rickshaw.Graph.HoverDetail({ 
      	    graph: graph,
      	    xFormatter: function(x) { 
      	      return new Date(x * 60 * 60 * 24 * 1000).format("ddd mmmm d, yyyy") 
      	    },
      	    yFormatter: function(y) { return (y*100).toFixed(2) + "%"}
      	  });
      	  var legend = new Rickshaw.Graph.Legend({
              graph: graph,
              element: document.querySelector('#legend')
          });
          var shelving = new Rickshaw.Graph.Behavior.Series.Toggle({
              graph: graph,
              legend: legend
          });
          var highlighter = new Rickshaw.Graph.Behavior.Series.Highlight({
              graph: graph,
              legend: legend
          });
          var yAxis = new Rickshaw.Graph.Axis.Y({
              graph: graph,
              tickFormat: function(y) { return (y*100).toFixed(2) + "%"}
          });
          yAxis.render();
      	}
      } );
    }, 'json');
    
If you're interested in seeing the leaderboard in all it's beauty, check it out [here](http://memeorandum.herokuapp.com).

If you have any questions about the code, feel free to ask in the comments! Oh, and check out [Rickshaw](http://code.shutterstock.com/rickshaw/)—it's awesome.