---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults
title:      Dave Banerjee
layout:     home
cover:      true
permalink: 
---

Welcome! I am a third-year undergraduate student at Columbia University studying computer science, and I care about making the world a better place, especially for non-human animals. My academic interests lie in ethics, artificial intelligence, nanomaterials, and rationality. I hope my studies better equip me to tackle issues like factory farming, wild animal welfare, global governance, and existential risks.

You can learn more about me [here](/about).\
You can email me [here](mailto:dave.banerjee1@gmail.com).\
You can book a meeting with me <a href="https://zcal.co/davebanerjee1" target="_blank">here</a>.

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
        <span class="read-time">{{ post.read_time }}</span>
      </div>
    {% endif %}
  {% endfor %}
</div>

<!-- OLD WAY TO DISPLAY FEATURED POSTS -->
<!-- <h1>Featured Posts</h1>

<ul>
  {% for post in site.posts %}
    {% if post.featured %}
      <li>
        <h3><a href="{{ post.url }}">{{ post.title }}</a></h3>
        {{ post.subtitle }}
      </li>
    {% endif %}
  {% endfor %}
</ul> -->