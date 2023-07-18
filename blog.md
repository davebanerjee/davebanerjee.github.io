---
layout:      list
title:       Blog
permalink:   /blog/
---

<h1>Featured Posts</h1>

<div class="grid-container">
  {% for post in site.posts %}
    {% if post.featured %}
      <div class="blog-post">
        <a href="{{ post.url }}">
          <a href="{{ post.url }}"><img class="blog-post-img" src="{{ post.image }}" alt="{{ post.image_desc }}"></a>
          <h3 class="featured-post"><a href="{{ post.url }}">{{ post.title }}</a></h3>
          <span class="featured-post">{{ post.subtitle }}</span>
        </a>
      </div>
    {% endif %}
  {% endfor %}
</div>