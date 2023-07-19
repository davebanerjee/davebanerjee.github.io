---
layout:      list
title:       Blog
permalink:   /blog/
---

<h1>Featured Posts</h1>

<div class="grid-container">
  {% for post in site.posts %}
    {% if post.featured %}
      <div class="blog-post" onclick="window.location='{{ post.url }}';">
        <img class="blog-post-img" src="{{ post.image }}" alt="{{ post.image_desc }}">
        <h3 class="featured-post-title">{{ post.title }}</h3>
        <span class="featured-post-subtitle">{{ post.subtitle }}</span>
        <span class="read-time">{{ post.read_time }}</span>
      </div>
    {% endif %}
  {% endfor %}
</div>