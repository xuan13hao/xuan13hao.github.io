---
layout: page
title: Teaching
permalink: /teaching/
---

<div class="publications-page">
  <div class="teaching-list">
    {% for item in site.data.profile.teaching %}
    <div class="teaching-item">
      <p class="pub-title">{{ item.course }}</p>
    </div>
    {% endfor %}
  </div>
</div>
