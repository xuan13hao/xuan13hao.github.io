---
layout: page
title: Project
permalink: /talks/
---

<div class="talks-page">
  <section class="talks-section">
    <h2>Patents</h2>
    <ul class="talks-list">
      {% for item in site.data.talks.patents %}
      <li>
        <strong>{{ item.title }}</strong>. ({{ item.status }}).
      </li>
      {% endfor %}
    </ul>
  </section>

  <section class="talks-section">
    <h2>Working Papers</h2>
    <ul class="talks-list">
      {% for item in site.data.talks.working_papers %}
      <li>
        {{ item.authors }}. “<strong>{{ item.title }}</strong>”. ({{ item.year }}).
      </li>
      {% endfor %}
    </ul>
  </section>

  <section class="talks-section">
    <h2>Selected Works in Progress</h2>
    <ul class="talks-list">
      {% for item in site.data.talks.works_in_progress %}
      <li>{{ item }}</li>
      {% endfor %}
    </ul>
  </section>
</div>
