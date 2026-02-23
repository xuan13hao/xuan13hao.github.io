---
layout: page
title: Selected Conference and Journal Review
permalink: /cv/
---

<div class="cv-page">
  <div class="reviews-list">
    {% for review in site.data.reviews %}
    <div class="review-item">
      <div class="review-name">
        {% if review.publisher %}
        <strong>{{ review.name }}</strong> – {{ review.publisher }}
        {% else %}
        <strong>{{ review.name }}</strong>
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

