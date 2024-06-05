---
layout: page
permalink: /posts
title: Valentine Gilbart's posts
---

# My posts

Sometimes I post about issues I've encountered... hopefully with some solutions! 

Check some of my posts here: 

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a> - {{ post.date | date: "%-d %B %Y" }} 
    </li>
  {% endfor %}
</ul>
