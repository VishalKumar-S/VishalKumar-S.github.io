---
layout: page
title: Projects
permalink: /projects/
description: My projects
nav: true
nav_order: 2

horizontal: false
---

<!-- pages/projects.md -->
<div class="projects">
{%- if site.enable_project_categories and page.display_categories %}
  <!-- Display categorized projects -->
  {%- for category in page.display_categories %}
  <h2 class="category">{{ category }}</h2>
  {%- assign categorized_projects = site.projects | where: "category", category -%}
  {%- assign projects_with_importance = categorized_projects | where_exp: "item", "item.importance != nil" %}

  {%- assign sorted_projects = projects_with_importance | sort: "importance" %}
  <!-- Generate cards for each project -->
  {% if page.horizontal -%}
  <div class="container">
    <div class="row row-cols-2">
    {%- for project in sorted_projects -%}
      {% include projects_horizontal.html %}
    {%- endfor %}
    </div>
  </div>
  {%- else -%}
  {%- if sorted_projects and sorted_projects.size > 0 -%}
  <!-- Iterate and display projects -->
    {%- for project in sorted_projects -%}
      {% include projects.html %}
    {%- endfor -%}
  {%- else -%}
    <p>No projects found.</p>
  {%- endif -%}

  <div class="grid">
    {%- for project in sorted_projects -%}
      {% include projects.html %}
    {%- endfor %}
  </div>
  {%- endif -%}
  {% endfor %}

{%- else -%}
<!-- Display projects without categories -->
  {%- assign projects_with_importance = site.projects | where_exp: "project", "project.importance != nil" %}
  {%- assign sorted_projects = projects_with_importance | sort: "importance" -%}
  <!-- Generate cards for each project -->
  {% if page.horizontal -%}
  <div class="container">
    <div class="row row-cols-2">
    {%- for project in sorted_projects -%}
      {% include projects_horizontal.html %}
    {%- endfor %}
    </div>
  </div>
  {%- else -%}
  <div class="grid">
    {%- for project in sorted_projects -%}
      {% include projects.html %}
    {%- endfor %}
  </div>
  {%- endif -%}
{%- endif -%}
</div>
