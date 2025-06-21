---
layout:           about
title:            About
permalink:        /about
---

My name is Dave Banerjee, and I am a summer fellow at the [Centre for the Governance of AI](https://www.governance.ai/), where I research [compute governance](). Previously, I was a participant in [ARENA 5.0](https://www.arena.education/), a 5-week ML alignment bootcamp. In my ARENA capstone project, I investigated whether self-perceived superintelligent LLMs (LLMs convinced that they are superintelligent via prompting) exhibit misalignment. And before that, I was a research fellow in the [SPAR program](https://sparai.org/), where I researched how much it costs to hack an Nvidia H100. And before that, I was a security engineer at a boutique hedge fund, where I built their security infrastructure from the ground up and led all security operations. I recently graduated from Columbia University in December 2024, where I studied computer science (among many other things).

My academic interests lie in AI safety & governance, hardware & software security, (meta)ethics, physics, and cognitive science. My primary goal is improve the welfare of sentient beings, and I think one of the best ways for securing a flourishing future is to ensure that the transition to world with transformative AI goes well.

On my blog, I share ideas I find cool and interesting. My primary goal with this blog is to formulate my opinions more carefully, critically evaluate my beliefs, and enhance my writing and research skills. Although I primarily write for myself, I hope you enjoy exploring my thoughts and learning more about the world alongside me.

In the projects section, I document my research projects, programming projects, and other longer-form intellectual projects.

In my free time, you can find me rock climbing, [reading](https://www.goodreads.com/user/show/136154707-dave-banerjee), thrifting, dancing, or folding laundry.

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