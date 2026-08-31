---
layout: page
title: projects
permalink: /projects/
description: Selected engineering and research projects in GPU computing, computer vision, and applied AI.
nav: true
nav_order: 3
display_categories: [research]
horizontal: false
---

<!-- pages/projects.md -->
<style>
  .project-card-link { text-decoration: none !important; color: inherit; display: block; height: 100%; }
  .project-card {
    height: 100%; display: flex; flex-direction: column; overflow: hidden;
    background-color: var(--global-card-bg-color); border: 1px solid var(--global-divider-color);
    border-radius: 0.75rem; transition: transform 0.2s ease, box-shadow 0.2s ease, border-color 0.2s ease;
  }
  .project-card:hover { transform: translateY(-4px); box-shadow: 0 10px 24px rgba(0, 0, 0, 0.12); border-color: var(--global-theme-color); }
  .project-card-img { aspect-ratio: 16 / 10; overflow: hidden; background-color: var(--global-code-bg-color); border-bottom: 1px solid var(--global-divider-color); }
  .project-card-img img { width: 100%; height: 100%; object-fit: cover; display: block; }
  .project-card-img figure, .project-card-img picture { width: 100%; height: 100%; margin: 0; display: block; }
  .project-card-placeholder { width: 100%; height: 100%; display: flex; align-items: center; justify-content: center; font-size: 2.5rem; color: var(--global-theme-color); opacity: 0.55; }
  .project-card-body { display: flex; flex-direction: column; flex-grow: 1; padding: 1.1rem 1.2rem 1.2rem; }
  .project-card-title { font-size: 1.06rem; font-weight: 600; line-height: 1.35; margin: 0 0 0.5rem; color: var(--global-text-color); }
  .project-card-desc { font-size: 0.88rem; line-height: 1.5; color: var(--global-text-color-light); margin: 0 0 0.9rem; }
  .project-card-more { margin-top: auto; font-size: 0.82rem; font-weight: 600; color: var(--global-theme-color); }
  .project-card-more i { font-size: 0.72rem; margin-left: 0.25rem; transition: transform 0.2s ease; }
  .project-card:hover .project-card-more i { transform: translateX(3px); }
  .projects h2.category { margin-bottom: 1.25rem; }
</style>
<div class="projects">
{% if site.enable_project_categories and page.display_categories %}
  <!-- Display categorized projects -->
  {% for category in page.display_categories %}
  <a id="{{ category }}" href=".#{{ category }}">
    <h2 class="category">{{ category }}</h2>
  </a>
  {% assign categorized_projects = site.projects | where: "category", category %}
  {% assign sorted_projects = categorized_projects | sort: "importance" %}
  <!-- Generate cards for each project -->
  {% if page.horizontal %}
  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for project in sorted_projects %}
      {% include projects_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for project in sorted_projects %}
      {% include projects.liquid %}
    {% endfor %}
  </div>
  {% endif %}
  {% endfor %}

{% else %}

<!-- Display projects without categories -->

{% assign sorted_projects = site.projects | sort: "importance" %}

  <!-- Generate cards for each project -->

{% if page.horizontal %}

  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for project in sorted_projects %}
      {% include projects_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for project in sorted_projects %}
      {% include projects.liquid %}
    {% endfor %}
  </div>
  {% endif %}
{% endif %}
</div>
