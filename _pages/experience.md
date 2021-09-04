---
layout: page
permalink: /experience/
title: experience
description: work experience
nav: false
horizontal: false
---

<div class="experience">
  {% if site.enable_experience_categories and page.display_categories %}
  <!-- Display categorized experience -->
    {% for category in page.display_categories %}
      <h2 class="category">{{category}}</h2>
      {% assign categorized_experience = site.experience | where: "category", category %}
      {% assign sorted_experience = categorized_experience | sort: "importance" %}
      <!-- Generate cards for each experience -->
      {% if page.horizontal %}
        <div class="container">
          <div class="row row-cols-2">
          {% for experience in sorted_experience %}
            {% include experience_horizontal.html %}
          {% endfor %}
          </div>
        </div>
      {% else %}
        <div class="grid">
          {% for experience in sorted_experience %}
            {% include experience.html %}
          {% endfor %}
        </div>
      {% endif %}
    {% endfor %}

  {% else %}
  <!-- Display experience without categories -->
    {% assign sorted_experience = site.experience | sort: "importance" %}
    <!-- Generate cards for each experience -->
    {% if page.horizontal %}
      <div class="container">
        <div class="row row-cols-2">
        {% for experience in sorted_experience %}
          {% include experience_horizontal.html %}
        {% endfor %}
        </div>
      </div>
    {% else %}
      <div class="grid">
        {% for experience in sorted_experience %}
          {% include experience.html %}
        {% endfor %}
      </div>
    {% endif %}

  {% endif %}

</div>