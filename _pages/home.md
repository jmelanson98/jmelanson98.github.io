---
layout: page
title: home
permalink: /
display_categories: [projects, publications, repositories, teaching, outreach]
nav_exclude: false
nav_order: 1
hide_title: true
---
<style>
  /* Force right-align, dark color, and underline on category titles */
  h2.category {
    color: #222222 !important;                /* very dark gray */
    text-align: right !important;             /* right align */
    border-bottom: 2px solid #222222 !important; /* underline */
    padding-bottom: 0.3rem !important;        /* spacing below text */
    margin-bottom: 1rem !important;           /* spacing below underline */
  }
</style>



<!-- Hero Section -->
<div class="row align-items-center my-5">
  <div class="col-md-6">
    <h1 class="display-5">How do our farmlands impact pollinator health, behaviour, and persistence?</h1>
    <p class="lead" style="font-size: 1rem;">My research explores spatiotemporal patterns of bumblebee foraging, dispersal, disease, and pesticide exposure to assess how landscape-scale management shapes the risks and rewards experienced by pollinators in working landscapes. I aim to contribute to our understanding of the drivers of pollinator declines, improve predictions of pollinator abundance and diversity under different management scenarios, and inform future management and conservation actions.</p>
  </div>
  <div class="col-md-6">
    <img src="{{ site.baseurl }}/assets/img/huntii.HEIC" class="img-fluid rounded" alt="Research banner image">
  </div>
</div>


<div class="projects">
  {% if page.display_categories %}
    {% for category in page.display_categories %}
      <a id="{{ category }}" href="#{{ category }}">
        <h2 class="category">{{ category }}</h2>
      </a>

      {% assign categorized_pages = site.pages | where_exp: "p", "p.display_category == category" %}
      {% assign sorted_pages = categorized_pages | sort: "importance" %}

      {% if page.horizontal %}
        <div class="container">
          <div class="row row-cols-1 row-cols-md-2">
            {% for page_item in sorted_pages %}
              {% assign project = page_item %}
              {% include projects_horizontal.liquid %}
            {% endfor %}
          </div>
        </div>
      {% else %}
        <div class="row row-cols-1 row-cols-md-3">
          {% for page_item in sorted_pages %}
            {% assign project = page_item %}
            {% include projects.liquid %}
          {% endfor %}
        </div>
      {% endif %}
    {% endfor %}
  {% else %}
    {% assign sorted_pages = site.pages | sort: "importance" %}

    {% if page.horizontal %}
      <div class="container">
        <div class="row row-cols-1 row-cols-md-2">
          {% for page_item in sorted_pages %}
            {% assign project = page_item %}
            {% include projects_horizontal.liquid %}
          {% endfor %}
        </div>
      </div>
    {% else %}
      <div class="row row-cols-1 row-cols-md-3">
        {% for page_item in sorted_pages %}
          {% assign project = page_item %}
          {% include projects.liquid %}
        {% endfor %}
      </div>
    {% endif %}
  {% endif %}
</div>
