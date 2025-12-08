---
layout: page
title: Projects
permalink: /projects/
---

Here are some of the projects I've worked on! Click on any project to learn more.

<div class="project-gallery">
  {% assign sorted_projects = site.projects | sort: "date" | reverse %}
  {% for project in sorted_projects %}
    <div class="project-card">
      <a href="{{ project.url | relative_url }}">
        {% if project.image %}
          <img src="{{ project.image | relative_url }}" alt="{{ project.title }} thumbnail">
        {% else %}
          <img src="{{ '/assets/images/download.png' | relative_url }}" alt="Placeholder image">
        {% endif %}
        <h3>{{ project.title }}</h3>
      </a>
    </div>
  {% endfor %}
</div>