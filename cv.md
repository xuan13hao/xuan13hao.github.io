---
layout: page
title: Academic Services
permalink: /cv/
---

<div class="cv-page">
  <div class="reviews-list">
    {% for review in site.data.reviews %}
    <div class="review-item">
      <div class="review-name">
        {% if review.publisher %}
        {{ review.name }} – {{ review.publisher }}
        {% else %}
        {{ review.name }}
        {% endif %}
      </div>
      <div class="review-years">
        {% assign years_str = review.years | join: ", " %}
        {{ years_str }}
      </div>
    </div>
    {% endfor %}
  </div>
</div>

