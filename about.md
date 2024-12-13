---
layout:           about
title:            About
permalink:        /about
---

My name is Dave Banerjee, and I am a fourth-year undergraduate student studying computer science at Columbia University in New York. My academic interest interests lie in information security, AI, ethics, physics, and cognitive science, but these interests are always subject to change. I have a research background in physics and AI explainability. I have since shifted my focus towards philosophy and AI security. I think studying philosophy and AI security will equip me with the tools to tackle some of the world's most pressing problems. Some problems I care an awful lot about include AI safety, wild animal welfare, and factory farming.

On my blog, I share ideas I find cool and interesting. My primary goal with this blog is to formulate my opinions more carefully, critically evaluate my beliefs, and enhance my writing and research skills. Although I primarily write for myself, I hope you enjoy exploring my thoughts and learning more about the world alongside me.

In the projects section, I document my research projects, programming projects, and other longer-form intellectual projects.

In my free time, you can find me rock climbing, going to raves, [reading](https://www.goodreads.com/user/show/136154707-dave-banerjee), thrifting, dancing, or folding laundry.

If you would like to receive emails whenever I post: <a href="https://mailchi.mp/fb3001298fbe/issic5ngxf" style="text-decoration: none" class="shortcode-text-button__button" target="_blank">Subscribe Here!</a>

I hope you enjoy exploring my site :)

— Dave

---

<h1>Featured Posts</h1>

<div class="grid-container">
  {% for post in site.posts %}
    {% if post.featured %}
      <div class="blog-post" onclick="window.location='{{ post.url }}';">
        <img class="blog-post-img" src="{{ post.image }}" alt="{{ post.image_desc }}">
        <h3 class="featured-post-title">{{ post.title }}</h3>
        <span class="featured-post-subtitle">{{ post.subtitle }}</span>
        <span class="readable-date">{{ post.readable_date }}</span>
        <span class="read-time">{{ post.read_time }} </span>
      </div>
    {% endif %}
  {% endfor %}
</div>