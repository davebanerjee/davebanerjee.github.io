---
layout:           page
title:            Projects
permalink:        /projects
---

<div class="grid-container">
  {% for post in site.posts %}
    {% if post.project %}
      <div class="blog-post" onclick="window.location='{{ post.url }}';">
        <img class="blog-post-img" src="{{ post.image }}" alt="{{ post.image_desc }}">
        <h3 class="featured-post-title">{{ post.title }}</h3>
        <span class="featured-post-subtitle">{{ post.subtitle }}</span>
        <span class="readable-date">{{ post.readable_date }}</span>
      </div>
    {% endif %}
  {% endfor %}
</div>