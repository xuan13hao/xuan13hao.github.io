---
layout: page
title: Publications
permalink: /publications/
hide_title: true
---

<div class="publications-page">
<h2 class="publications-page">Papers</h2>
  <div class="filter-controls">
    <button class="filter-btn active" data-filter="all">All</button>
    <button class="filter-btn" data-filter="selected">Selected</button>
  </div>

  {% assign sorted_pubs = site.data.publications | sort: "year" | reverse %}
  {% assign years = sorted_pubs | map: "year" | uniq | sort | reverse %}

  {% for year in years %}
  <section class="publication-year-section">
    <h2 class="year-header">{{ year }}</h2>
    <div class="publications-list">
      {% for pub in sorted_pubs %}
        {% if pub.year == year %}
        <div class="publication-card" data-selected="{{ pub.selected }}">
          <p class="pub-title">{{ pub.title }}</p>
          <p class="pub-authors">
            {% assign authors = pub.authors | split: ", " %}
            {% for author in authors %}
              {% assign author_trimmed = author | strip %}
              {% assign should_bold = false %}
              {% if author_trimmed == "Hao Xuan" %}
                {% assign should_bold = true %}
              {% elsif author_trimmed contains "Xuan, H" %}
                {% assign should_bold = true %}
              {% elsif author_trimmed contains "H. Xuan" %}
                {% assign should_bold = true %}
              {% endif %}
              {% if should_bold %}
                <strong>{{ author_trimmed }}</strong>{% unless forloop.last %}, {% endunless %}
              {% else %}
                {{ author_trimmed }}{% unless forloop.last %}, {% endunless %}
              {% endif %}
            {% endfor %}
          </p>
          <p class="pub-venue">
            <em>{{ pub.venue }}</em>
            {% if pub.type %}<span class="pub-type">{{ pub.type }}</span>{% endif %}
          </p>
          <div class="pub-links">
            {% if pub.doi %}
            <a href="{{ pub.doi }}" target="_blank" rel="noopener noreferrer">DOI</a>
            {% endif %}
            {% if pub.pdf %}
            <a href="{{ pub.pdf | relative_url }}">PDF</a>
            {% endif %}
            {% if pub.code %}
            <a href="{{ pub.code }}" target="_blank" rel="noopener noreferrer">Code</a>
            {% endif %}
          </div>
        </div>
        {% endif %}
      {% endfor %}
    </div>
  </section>
  {% endfor %}

  <section class="review-section">
    <h2 class="year-header">Academic Services</h2>
    
    {% assign journal_reviews = site.data.reviews | where: "type", "journal" %}
    {% if journal_reviews.size > 0 %}
    <div class="review-category">
      <h3 class="review-category-title">Journal Reviewer</h3>
      <div class="reviews-list">
        {% for review in journal_reviews %}
        <div class="review-item">
          <div class="review-name">
            {% if review.publisher %}
            {{ review.name }} – {{ review.publisher }}
            {% else %}
            {{ review.name }}
            {% endif %}
          </div>
        </div>
        {% endfor %}
      </div>
    </div>
    {% endif %}
    
    {% assign conference_reviews = site.data.reviews | where: "type", "conference" %}
    {% if conference_reviews.size > 0 %}
    <div class="review-category">
      <h3 class="review-category-title">Conference Reviewer</h3>
      <div class="reviews-list">
        {% for review in conference_reviews %}
        <div class="review-item">
          <div class="review-name">
            {% if review.publisher %}
            {{ review.name }} – {{ review.publisher }}
            {% else %}
            {{ review.name }}
            {% endif %}
          </div>
        </div>
        {% endfor %}
      </div>
    </div>
    {% endif %}
  </section>
</div>

<script>
  document.addEventListener('DOMContentLoaded', function() {
    const filterButtons = document.querySelectorAll('.filter-btn');
    const publicationCards = document.querySelectorAll('.publication-card');
    
    filterButtons.forEach(button => {
      button.addEventListener('click', function() {
        const filter = this.getAttribute('data-filter');
        
        // Update active button
        filterButtons.forEach(btn => btn.classList.remove('active'));
        this.classList.add('active');
        
        // Filter publications
        publicationCards.forEach(card => {
          if (filter === 'all') {
            card.style.display = '';
          } else if (filter === 'selected') {
            const isSelected = card.getAttribute('data-selected') === 'true';
            card.style.display = isSelected ? '' : 'none';
          }
        });
      });
    });
  });
</script>
