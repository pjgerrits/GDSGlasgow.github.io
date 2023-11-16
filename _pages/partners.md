---
layout: page
title: partners
permalink: /partners/
description: our research partners
nav: true
nav_order: 3.1
display_categories: 
horizontal: false
---

<!-- pages/partners.md -->
<div class="partners">
{%- if site.enable_partner_categories and page.display_categories %}
  <!-- Display categorized partners -->
  {%- for category in page.display_categories %}
  <h2 class="category">{{ category }}</h2>
  {%- assign categorized_partners = site.partners | where: "category", category -%}
  {%- assign sorted_partners = categorized_partners | sort: "importance" %}
  <!-- Generate cards for each partner -->
  {% if page.horizontal -%}
  <div class="container">
    <div class="row row-cols-2">
    {%- for partner in sorted_partners -%}
      {% include partners_horizontal.html %}
    {%- endfor %}
    </div>
  </div>
  {%- else -%}
  <div class="grid">
    {%- for partner in sorted_partners -%}
      {% include partners.html %}
    {%- endfor %}
  </div>
  {%- endif -%}
  {% endfor %}

{%- else -%}
<!-- Display partners without categories -->
  {%- assign sorted_partners = site.partners | sort: "importance" -%}
  <!-- Generate cards for each partner -->
  {% if page.horizontal -%}
  <div class="container">
    <div class="row row-cols-2">
    {%- for partner in sorted_partners -%}
      {% include partners_horizontal.html %}
    {%- endfor %}
    </div>
  </div>
  {%- else -%}
  <div class="grid">
    {%- for partner in sorted_partners -%}
      {% include partners.html %}
    {%- endfor %}
  </div>
  {%- endif -%}
{%- endif -%}
</div>
