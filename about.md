---
layout: about
title:  About
---

My name is Dave Banerjee, and I am a third-year undergraduate studying computer science at Columbia University in New York. My academic interest interests lie in ethics, artificial intelligence, nanomaterials, and rationality, but these interests are always subject to change. I have a research background in physics, more specificially nanomaterials, and have worked in the field for three years. I have since pivoted away from physics towards philosophy and artificial intelligence. I think philosophy and artificial intelligence have a pretty good chance of equipping me with the tools to better tackle some of the world's most pressing problems. Some problems I care an awful lot about include factory farming, wild animal welfare, global governance,and existential risks.

On my blog, I share any and all ideas I find cool and interesting. My primary goal with this blog is to formulate my opinions more carefully, critically evaluate my beliefs, and enhance my writing and research skills. Although I primarilly write for personal growth, I hope you enjoy exploring my thoughts.

In the projects section, I document my research projects, programming projects, and other longer-form intellectual projects.

In my free time, you can find me rock climbing, attending EDM concerts, [reading](https://www.goodreads.com/user/show/136154707-dave-banerjee), thrifting, dancing, or folding laundry.

I hope you enjoy exploring my site :)

— Dave

---

<h2>Featured Posts</h2>

<ul>
  {% for post in site.posts %}
    <li>
      <h3><a href="{{ post.url }}">{{ post.title }}</a></h3>
      {{ post.excerpt }}
    </li>
  {% endfor %}
</ul>