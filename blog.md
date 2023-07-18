---
layout: list
title: Blog
permalink: /blog/
---

<h1>Featured Posts</h1>

<ul>
  {% for post in site.posts %}
    {% if post.featured %}
      <li>
        <h3><a href="{{ post.url }}">{{ post.title }}</a></h3>
        {{ post.description }}
      </li>
    {% endif %}
  {% endfor %}
</ul>