---
layout: page
title: Jesse Pollak
tagline: Discussing what comes to mind
---
{% include JB/setup %}


I’m Jesse Pollak, a rising sophomore at Pomona College outside of Los Angeles. This summer, I’m a hackNY Fellow and technical intern at BuzzFeed. I’m living in Union Square, working in the Flatiron District, gradually finding my way around NYC, and hoping to learn as much as possible (about anything and everything). Some of my past projects include <a href='http://likesecret.com'>Like Secret</a>, <a href='http://5crideshare.com'>5C Ride Share app</a> and the <a href='http://freegamenotifier.herokuapp.com/'>MLB.tv Free Game of the Day notifier</a>.

Follow me on <a href='http://twitter.com/jessepollak'>Twitter</a>, friend me on <a href='http://facebook.com/jessepollak'>Facebook</a>, and fork my code on <a href='http://github.com/jpollak92'>Github</a>. Oh, and **read my blog**:

</br>

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

