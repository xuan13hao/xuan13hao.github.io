---
layout: page
title: Curriculum Vitae
permalink: /cv/
---

<div class="cv-page">
  <div class="cv-header">
    <h1>{{ site.data.profile.name }}</h1>
    <div class="cv-contact">
      {% if site.data.profile.email %}
      <p><strong>Email:</strong> <a href="mailto:{{ site.data.profile.email }}">{{ site.data.profile.email }}</a></p>
      {% endif %}
      {% if site.data.profile.phone %}
      <p><strong>Phone:</strong> {{ site.data.profile.phone }}</p>
      {% endif %}
      {% if site.data.profile.github %}
      <p><strong>GitHub:</strong> <a href="{{ site.data.profile.github }}" target="_blank" rel="noopener noreferrer">{{ site.data.profile.github }}</a></p>
      {% endif %}
      {% if site.data.profile.cv_pdf %}
      <p><a href="{{ site.data.profile.cv_pdf | relative_url }}" class="btn" download>Download PDF</a></p>
      {% endif %}
    </div>
  </div>

  <section class="cv-section">
    <h2>Summary</h2>
    <div class="cv-content">
      {{ site.data.profile.bio | markdownify }}
    </div>
  </section>

  <section class="cv-section">
    <h2>Education</h2>
    <div class="cv-content">
      {% for edu in site.data.profile.education %}
      <div class="cv-item">
        <h3>{{ edu.degree }}</h3>
        <p class="cv-institution">{{ edu.institution }}</p>
        <p class="cv-year">{{ edu.year }}</p>
        {% if edu.advisor %}
        <p class="cv-detail">Advisor: {{ edu.advisor }}</p>
        {% endif %}
      </div>
      {% endfor %}
    </div>
  </section>

  <section class="cv-section">
    <h2>Research Interests</h2>
    <div class="cv-content">
      <ul>
        {% for interest in site.data.profile.interests %}
        <li>{{ interest }}</li>
        {% endfor %}
      </ul>
    </div>
  </section>

  <section class="cv-section">
    <h2>Publications</h2>
    <div class="cv-content">
      {% assign sorted_pubs = site.data.publications | sort: "year" | reverse %}
      {% for pub in sorted_pubs %}
      <div class="cv-item">
        <p><strong>{{ pub.title }}</strong></p>
        <p>{{ pub.authors }}</p>
        <p><em>{{ pub.venue }}</em>{% if pub.year %} ({{ pub.year }}){% endif %}</p>
      </div>
      {% endfor %}
    </div>
  </section>

  <section class="cv-section">
    <h2>Projects</h2>
    <div class="cv-content">
      {% for project in site.data.projects %}
      <div class="cv-item">
        <h3>{{ project.title }}</h3>
        <p>{{ project.description }}</p>
      </div>
      {% endfor %}
    </div>
  </section>
</div>
