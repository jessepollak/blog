---
layout: post
title: "Replicating Stripe's pay with Stripe button"
description: ""
category:
tags: []
---
{% include JB/setup %}

[Stripe](https://stripe.com) is an awesome company, I think we can all agree on that. Not only do they allow any website to accept payments with reasonable charge fees, they make it easy and beautiful. One of their latest projects, the [Pay With Stripe button](https://stripe.com/docs/button), is the definition of their greatness: a super simple installation, the same rates as usual, and a beautiful user experience.

At [Clef](https://clef.io), we are building a client side javascript library that involves a similar developer setup experience and were really impressed with how easy it is for any developer to get the button on their site.All it takes in one script tag:

{% highlight html %}
<script src="https://button.stripe.com/v1/button.js"
        class="stripe-button"
        data-key="pk_AmVHPHd4LGNUjdm1duBlMt5lMtdJU"></script>
{% endhighlight %}

No adding random divs, no initialization, just a simple script tag. We loved it, so we [implemented a similar process for Clef](https://developer.clef.io/information#started). It was surprisingly easy, so I thought I'd do a quick writeup of how to create script tag like Stripe.

The key to the strategy is including a class on the script tag. Since the script element has this tag, you can select it inside of itself. Let's create a similar script tag:

{% highlight html %}

<script src="script.js" class="script-class" data-type='h3'>
</script>

{% endhighlight %}
Now, inside of `script.js` we can select the script tag, parse its data attributes, and run whatever code we need to:

{% highlight javascript linenos %}

var scriptTag = document.querySelector('.script-class');
if(!scriptTag) {
    //take appropriate action
} else {
    var type = scriptTag.getAttribute('data-type');
    var element = document.createElement(type);
    var text = document.createTextNode('Text in a ' + type);
    element.appendChild(text);
    scriptTag.parentNode.insertBefore(element, scriptTag);
}

{% endhighlight %}

That snippet of code will find the script tag and insert a DOM element of type `type` before it in the DOM with the content we specified. Pretty cool, eh?

<p class='endnote'>Big thanks to <a href='https://stripe.com'>Stripe</a> for the inspiration and <a href='https://github.com/landakram'>Mark Hudnall</a> for help with the implementation.</p>