---
layout: post
title: "Using flask-mail with multiple accounts"
description: ""
category: 
tags: []
---
{% include JB/setup %}

For the last 3 months, I've been hacking away on [Clef](https://clef.io)--a new identity platform for the web that replaces usernames and passwords with a user's mobile phone. We've written the majority of the backend for [Clef](https://clef.io) in Python using the Flask framework; giving me the chance to start learning the intricacies of both.

A couple weeks ago, we decided to revamp the way we handle emailing users, so we could add easy lifecycle emailing. For convenience, we decided to build our email system on the [flask-mail](http://packages.python.org/Flask-Mail/) package. For the most part, this little piece of software (~500 LOC) has served its purpose, but as with almost any open source library, we had to do a little messing around to get it to do exactly what we wanted.

The primary problem was that we wanted our lifecycle emails to come from our CEO (Brennen), but everything else to come from a standard 'info@clef.io' email address. Unfortunately, [flask-mail](http://packages.python.org/Flask-Mail/) out of the box only allows for emails to be sent from one account.

After looking at the source, however, we realized that this was an easily overridable restriction--account information was stored in public variables in the [flask-mail Mail object](https://github.com/mattupstate/flask-mail/blob/master/flask_mail.py#L339). Plus, a reference to the Flask application the Mail object was bound to is stored in a public variable as well, so we can use the Flask application configuration file to store the alternate account information. Accordingly, it was as simple as saving the old account information, switching in the new information, then rewriting the old information:

{% highlight python linenos %}
mail = Mail(flask_app)
...
(username, password) = (mail.username, mail.password)
mail.username = mail.app.config.get('LIFECYCLE_USERNAME')
mail.password = mail.app.config.get('LIFECYCLE_PASSWORD')
mail.send(msg)
(mail.username, mail.password) = (username, password)

{% endhighlight %}

Definitely not a crazy solution, but I figured it was worth sharing with the internet (I Google'd and couldn't find anything).

*Do you know a better way to do this? Let me know in the comments!*