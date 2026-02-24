---
layout: page
title: Projects
permalink: /talks/
hide_title: true
---

<div class="publications-page">
  
  <section class="publication-year-section">
    <h2 class="year-header">Patents</h2>
    <div class="publications-list">
      {% for item in site.data.talks.patents %}
      <div class="publication-card">
        <p class="pub-title">{{ item.title }}. ({{ item.status }}).</p>
      </div>
      {% endfor %}
    </div>
  </section>

  <section class="publication-year-section">
    <h2 class="year-header">Working Projects</h2>
    <div class="publications-list">
      {% for item in site.data.talks.working_papers %}
      <div class="publication-card">
        <p class="pub-title">{{ item.title }}</p>
        <p class="pub-authors">{{ item.authors }}</p>
        <p class="pub-venue"><em>({{ item.year }})</em></p>
      </div>
      {% endfor %}
    </div>
  </section>
</div>
