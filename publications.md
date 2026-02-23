---
layout: page
title: Publications
permalink: /publications/
---

<div class="publications-page">
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
          <h3 class="pub-title">{{ pub.title }}</h3>
          <p class="pub-authors">{{ pub.authors }}</p>
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
