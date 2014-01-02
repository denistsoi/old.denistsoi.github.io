---
layout: page
title: Welcome to DenisTsoi.github.io!
tagline: ""
---

<ul class="posts">
  {% for post in site.posts limit: 5 %}
    <li>
    	<span>{{ post.date | date_to_string }} &raquo;</span> 
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>