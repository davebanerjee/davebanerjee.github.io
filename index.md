---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults
title: Dave Banerjee
layout: home
cover: true
---

Welcome! My name is **Dave Banerjee**, and I'm a third-year at Columbia University. On my blog, I write about philosophy, programming, physics, personal life, rationality, and whatever else I find interesting. I like rock climbing, EDM concerts, [reading](https://www.goodreads.com/user/show/136154707-dave-banerjee), thrifting, dancing, and folding laundry. You can learn more about me [here](/about). You can contact me at [dave.banerjee1@gmail.com](mailto:dave.banerjee1@gmail.com). Book a meeting with me [here](https://zcal.co/davebanerjee1).

![Dave hoodie portrait](/low_library_roof_cropped.jpg)

---

<h1>Featured Posts</h1>

<ul>
  {% for post in site.posts %}
    <li>
      <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
      {{ post.excerpt }}
    </li>
  {% endfor %}
</ul>