---
layout: page
title: Teaching
permalink: /teaching/
---

<div class="teaching-page">
  <h2>Teaching Experience</h2>
  
  <div class="teaching-list">
    {% for item in site.data.profile.teaching %}
    <div class="teaching-item">
      <h3>{{ item.course }}</h3>
      <p class="teaching-role">{{ item.role }}</p>
      <p class="teaching-period">{{ item.period }}</p>
      {% if item.description %}
      <p class="teaching-description">{{ item.description }}</p>
      {% endif %}
    </div>
    {% endfor %}
  </div>
</div>
