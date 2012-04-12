---
layout: page
title: Jesse Pollak
tagline: Discussing what comes to mind
---
{% include JB/setup %}

<h1>Blog posts</h1>

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

