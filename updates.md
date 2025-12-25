---
layout: default
title: Updates
permalink: /updates/
---
    
<div class="wrapper">
  <h1 class="page-heading">All Updates</h1>

  <div class="updates-feed">
    {% assign sorted_updates = site.updates | sort: 'date' | reverse %}
    {% for update in sorted_updates %}
      <article class="update-item">
        
        <header class="update-header">
          <div class="update-page-date">
            {% if update.format == "month_year" %}
              {{ update.date | date: "%B %Y" }}
            {% else %}
              {{ update.date | date: "%b %d, %Y" }}
            {% endif %}
          </div>
          <h2 class="update-page-description">{{ update.description }}</h2>
        </header>

        <div class="update-full-content">
          {{ update.content }}
        </div>

      </article>
      <hr class="update-separator">
    {% endfor %}
  </div>
</div>