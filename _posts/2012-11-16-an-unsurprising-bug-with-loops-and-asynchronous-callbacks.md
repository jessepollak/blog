---
layout: post
title: "An unsurprising bug with loops and asynchronous callbacks"
description: ""
category: 
tags: []
---
{% include JB/setup %}

Two weeks ago, at the [2nd Bi Annual 5C Hackathon](http://5chackathon.com), I built [GitBattle](http://gitbattle.com) with [Remy G](http://twitter.com/datarem). While we ended up winning the People's Choice Award, the learning experience was way more important. Over the next week or so, I'm going to be doing a few posts that together will form a sort of post mortem on the expereience. Today, since it's Friday, I'll be writing on one of the shorter, but still tricky, topics.

When I started building [GitBattle](http://gitbattle.com), I decided that I would do no processing on the server side. Essentially, I wanted to do every API request to the Github API, all the data processing, and all of the graph generation in javascript on the client side. In order for this to happen, and have the browser not lock up, I had to impose one simple restriction on myself: no *synchronous* AJAX calls. In the end, this meant that over the course of processing two usernames, I'd often do 100+ asynchronous AJAX calls (I maxed out at ~500 for two big repos). I'll go into the particulars of how I synchronized all of those in a later post, but while writing a simple part of that process, I encountered a bug I'd never seen before.

Before I ran the bulk of the API requests and data processing, I needed to confirm that the two entered usernames were valid, so I ran this chunk of code:

{% highlight javascript linenos %}
for(var i = 0; i < users.length; i++) {
  if(users[i] == "") {
      //make UI changes for invalid user and return
  } else {
    promises.push($.Deferred(function(def) {
      $.ajax({
        url: GITHUB + 'users/' + users[i] 
        + IDENTITY + '&callback=?',
        success: function(data) {
          if (data.data && data.data.message == "Not Found") {
              $(form['user_' + i])
              .css('border', '5px solid rgb(186, 0,0)');
              fail = true;
          }
          def.resolve();
        },
        dataType: 'jsonp'
      });
    }));  
  }
}

$.when.apply(null, promises).done(function () {
  if(fail) {
      //make UI change for invalid user and return
  } else {
      ...valid, so do the rest of the processing
  }
}

{% endhighlight %}

In the `for` loop, I iterated over the usernames (which I had already gotten from the form fields), first checked if they were empty (and therefore invalid), and then did an asynchronous AJAX request to check if they were valid Github usernames and stored the promise for that request. In the AJAX callback, I checked if they were valid and if they weren't did the appropriate UI changes to indicate failure and returned false. If you haven't wrapped your ahead around promises and `$.Deferred` yet, don't worry--that's unimportant to this bug.

With this code, I was correctly identifying invalid Github users and returning false before any other processing, but the valid UI changes were not being implemented. Eventually, I realized that this was happening because the `i` in the line:

{% highlight javascript %}

$(form['user_' + i]).css('border', '5px solid rgb(186, 0,0)');

{% endhighlight %}

was scoped in the for loop. Therefore, when the AJAX callback ran, the for loop had already been iterated all the way through and `i` was at 2 (and we only had user_0 and user_1). For a quick fix, I added a `key` variable which stored the value of `i` and was scoped inside of the deferred object--meaning it's value never changed. Problem solved!

{% highlight javascript %}

...
promises.push($.Deferred(function(def) {
  key = i;
  $.ajax({
    url: (GITHUB + 'users/' + users[i] +
    IDENTITY + '&callback=?',
    success: function(data) {
      if (data.data && data.data.message == "Not Found") {
        $(form['user_' + key])
          .css('border', '5px solid rgb(186, 0,0)');
        fail = true;
      }
      def.resolve();
    },
    dataType: 'jsonp'
  });
})); 
...

{% endhighlight %}