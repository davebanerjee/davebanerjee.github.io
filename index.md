---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults
title:      Dave Banerjee
layout:     page
cover:      true
permalink: 
---

Welcome! I am a summer fellow at [Centre for the Governance of AI](https://www.governance.ai/), where I research [compute governance](https://bluedot.org/blog/introduction-to-compute-governance). Previously, I was a participant in [ARENA 5.0](https://www.arena.education/), hardware security research assistant through the [SPAR program](https://sparai.org/), and security engineer at a hedge fund. I recently graduated from Columbia University in December 2024, where I studied computer science. 

My academic interests lie in AI safety & governance, hardware & software security, (meta)ethics, physics, and cognitive science. My primary goal is improve the welfare of sentient beings, and I think one of the best ways for securing a flourishing future is to ensure that the transition to world with transformative AI goes well. I'm also interested in issues like [wild animal welfare](https://forum.effectivealtruism.org/topics/wild-animal-welfare#:~:text=Wild%20animal%20welfare%20is%20the,by%20several%20orders%20of%20magnitude) and [factory farming](https://thehumaneleague.org/article/what-is-factory-farming).

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