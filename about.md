---
layout:           about
title:            About
permalink:        /about
---

My name is Dave Banerjee, and I am a third-year undergraduate student studying computer science at Columbia University in New York. My academic interest interests lie in ethics, artificial intelligence, nanomaterials, and rationality, but these interests are always subject to change. I have a research background in physics, more specificially nanomaterials, and have worked in the field for three years. I have since shifted my focus towards philosophy and artificial intelligence. I think studying philosophy and artificial intelligence will equip me with the tools to tackle some of the world's most pressing problems. Some problems I care an awful lot about include factory farming, wild animal welfare, global governance,and existential risks.

On my blog, I share ideas I find cool and interesting. My primary goal with this blog is to formulate my opinions more carefully, critically evaluate my beliefs, and enhance my writing and research skills. Although I primarilly write for myself, I hope you enjoy exploring my thoughts and learning more about the world alongside me.

In the projects section, I document my research projects, programming projects, and other longer-form intellectual projects.

In my free time, you can find me rock climbing, going to raves, [reading](https://www.goodreads.com/user/show/136154707-dave-banerjee), thrifting, dancing, or folding laundry.

I hope you enjoy exploring my site :)

— Dave

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