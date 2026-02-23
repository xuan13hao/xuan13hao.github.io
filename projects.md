---
layout: page
title: Projects
permalink: /projects/
---

<div class="projects-page">
  <div class="filter-controls">
    <button class="filter-btn active" data-filter="all">All</button>
    <button class="filter-btn" data-filter="featured">Featured</button>
  </div>

  <div class="projects-grid">
    {% for project in site.data.projects %}
    <div class="project-card" data-featured="{{ project.featured }}">
      {% if project.image %}
      <div class="project-image">
        <img src="{{ project.image | relative_url }}" alt="{{ project.title }}">
      </div>
      {% endif %}
      <div class="project-content">
        <h3 class="project-title">{{ project.title }}</h3>
        <p class="project-description">{{ project.description }}</p>
        {% if project.highlights %}
        <ul class="project-highlights">
          {% for highlight in project.highlights %}
          <li>{{ highlight }}</li>
          {% endfor %}
        </ul>
        {% endif %}
        <div class="project-links">
          {% if project.links.paper %}
          <a href="{{ project.links.paper }}" target="_blank" rel="noopener noreferrer">Paper</a>
          {% endif %}
          {% if project.links.code %}
          <a href="{{ project.links.code }}" target="_blank" rel="noopener noreferrer">Code</a>
          {% endif %}
          {% if project.links.demo %}
          <a href="{{ project.links.demo }}" target="_blank" rel="noopener noreferrer">Demo</a>
          {% endif %}
        </div>
      </div>
    </div>
    {% endfor %}
  </div>
</div>

<script>
  document.addEventListener('DOMContentLoaded', function() {
    const filterButtons = document.querySelectorAll('.filter-btn');
    const projectCards = document.querySelectorAll('.project-card');
    
    filterButtons.forEach(button => {
      button.addEventListener('click', function() {
        const filter = this.getAttribute('data-filter');
        
        // Update active button
        filterButtons.forEach(btn => btn.classList.remove('active'));
        this.classList.add('active');
        
        // Filter projects
        projectCards.forEach(card => {
          if (filter === 'all') {
            card.style.display = '';
          } else if (filter === 'featured') {
            const isFeatured = card.getAttribute('data-featured') === 'true';
            card.style.display = isFeatured ? '' : 'none';
          }
        });
      });
    });
  });
</script>
