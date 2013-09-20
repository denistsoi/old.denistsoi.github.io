---
layout: page
title: Welcome to DenisTsoi.github.io!
tagline: ""
---

<ul class="posts">
  {% for post in site.posts limit: 5 %}
    <li>
    	<span>{{ post.date | date_to_string }}</span> &raquo; 
      <a href="{{ post.url }}">{{ post.title }}</a>
      <span>{{ post.excerpt }}</span>
    </li>
  {% endfor %}
</ul>