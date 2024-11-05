---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults
title:      Dave Banerjee
layout:     page
cover:      true
permalink: 
---

Welcome! I am a fourth-year undergraduate student at Columbia University studying computer science, and I care about making the world a better place, especially for non-human animals. My academic interests lie in information security, artificial intelligence, ethics, physics, and cognitive science. I hope my studies better equip me to tackle issues like AI safety, information security of critical infrastructure, wild animal welfare, and factory farming.

You can learn more about me [here](/about).\
You can email me [here](mailto:dave.banerjee1@gmail.com).\
You can book a meeting with me <a href="https://zcal.co/davebanerjee1" target="_blank">here</a>.\
If you want to receive emails everytime I post: <a href="https://mailchi.mp/fb3001298fbe/issic5ngxf" style="text-decoration: none" class="shortcode-text-button__button" target="_blank">Subscribe Here!</a>

---

![Dave hoodie portrait](/assets/low_library_roof_cropped.jpg)

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