---
layout: page
title: Blog
permalink: /blog/
---

<div class="blog-page">
  {% if site.posts.size > 0 %}
    <ul class="blog-list">
      {% for post in site.posts %}
      <li class="blog-item">
        <article>
          <h2><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h2>
          <time datetime="{{ post.date | date: '%Y-%m-%d' }}">{{ post.date | date: "%B %d, %Y" }}</time>
          {% if post.excerpt %}
          <div class="excerpt">{{ post.excerpt }}</div>
          {% endif %}
        </article>
      </li>
      {% endfor %}
    </ul>
  {% else %}
    <p class="no-posts">No blog posts yet. Check back soon!</p>
  {% endif %}
</div>
