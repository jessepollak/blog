---
layout: post
title: "Let's secure security defaults together"
description: ""
category: 
tags: []
---
{% include JB/setup %}

Today, an [article on authenticated encryption](http://tonyarcieri.com/all-the-crypto-code-youve-ever-written-is-probably-broken) hit the front page of Hacker News. Seeing as I'm working right now to implement a new, more secure, identity platform at [Clef](https://clef.io), it was interesting to use it test as a comparison tool to see what we were doing right (and wrong). After a thorough review by the team, we decided that we were in fact following the correct protocols in our phone <-> server interactions (although, this article doesn't exactly apply to our situation). What the article did expose, however, was a serious flaw in our server security, which I had overlooked...but my cofounders had already addressed.

I'll admit it: I'm not a security expert. I'm a self taught, primarily web focused developer who is trying to learn as much as possible about security (and everything, for that matter) in as short as time as possible (and that's why I'm not working on this company alone). But the fact that I overlooked this reasonably huge security flaw really reinforced in my mind some of the comments that were found in the [HN discussion](http://news.ycombinator.com/item?id=4779015). One stood out in particular, by [jarrett](http://news.ycombinator.com/user?id=jarrett):

> *Quite a few of the replies to acabal's comment amount to "yes, it's hard, suck it up and learn it."
>
> But the crypto community has told us time and again that we shouldn't be trying to learn the fine details of crypto. If we are, it's a warning sign we're wading into the dangerous world of actually implementing crypto. We're just supposed to use pre-built, peer-reviewed crypto systems and understand at a very high level how they work. E.g. knowing what a hash is versus symmetric keys vs asymmetric keys, knowing which algorithms are still acceptable (Bcrypt) and which aren't (md5). And this, I think, is the right message for developers.
>
> But the OP has a valid point. If it's true that many of the high-level, crypto-layman-friendly libraries do bad things like using all-zero IVs, then we have a real problem. But here's where I disagree with the OP: It should not fall on the average developer to understand this stuff and override a crypto library's insecure defaults.
>
> Instead, authors of crypto libraries need to step up and implement secure defaults, as well as provide solid documentation on the do's and don'ts of their libraries. (Assuming of course the OP is correct about the flawed defaults in existing libraries.)
>
> In any case, the solution is not to urge normal developers to learn crypto at the level the OP describes. I'm a smart guy, but I know better than to trust myself with things like initialization vectors. This is, after all, what the broader crypto community has been telling people.*

So, what was this security flaw? At [Clef](https://clef.io), we are using the [Flask micro framework](http://flask.pocoo.org) for our application server. [Flask](http://flask.pocoo.org) uses the [Werkzeug](http://werkzeug.pocoo.org) library to handle the majority of the heavy Request/Response heavy lifting and uses it's [Secure Cookie library](http://werkzeug.pocoo.org/docs/contrib/securecookie) by default. With a name like that, you might assume that they really are secure cookies, but if you scroll down their documentation, you see an [odd caveat](http://werkzeug.pocoo.org/docs/contrib/securecookie/#security):

> The default implementation uses Pickle as this is the only module that used to be available in the standard library when this module was created. If you have simplejson available it’s strongly recommended to create a subclass and replace the serialization method
>
> The weakness of Pickle is that if someone gains access to the secret key the attacker can not only modify the session but also execute arbitrary code on the server.

Yes, you read that right. If someone gets your secret key, many of which are [readily available on the interwebz](https://github.com/search?q=SECRET_KEY+flask&repo=&langOverride=&start_value=1&type=Code&language=Python), they can run **arbitrary code on your server**. And yet, because 'Pickle is the only module that **used** to be available in the standard library,' the simple fix (which includes json, which is now in the Python standard library) is not the default:

{% highlight python linenos %}

import json
from werkzeug.contrib.securecookie import SecureCookie

class JSONSecureCookie(SecureCookie):
    serialization_method = json

{% endhighlight %}

Here, the choices around defaults of the security experts who I assume implemented this cookie library have percolated through to a web framework used by thousands and thousands of developers and production applications. There's been [lots](http://stacksmashing.net/2012/08/10/dear-flask-please-fix-your-secure-cookies/) of [discussion](http://flask.pocoo.org/mailinglist/archive/2011/8/15/security-of-secure-sessions/) on the issue, and there is even a [Flask snippet](http://flask.pocoo.org/snippets/51/) with a fix, but no one has decided it is important enough to be 'defaultized.'

Yes, I understand that many developers will know about this issue, or read about it when they are starting with Flask, but I would venture a guess that just as many will not...and they will potentially expose themselves to a huge security risk.

And so, I'm left reiterating jarrett's point:

> Instead, authors of crypto libraries need to step up and implement secure defaults, as well as provide solid documentation on the do's and don'ts of their libraries.

Let's make the web a more secure web together.

<p class='endnote'>If you're wondering, Clef has made sure that our SECRET_KEY has never left the production server and that our cookies are stored in JSON. If you want to learn more about the identity platform that we are building, which replaces usernames and passwords with a user's mobile phone, check us out <a href='https://clef.io'>here</a></p>