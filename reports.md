---
layout: page
title: Reports & Presentations
permalink: /reports/
---

Here are some of my reports and presentations. Click an icon to view.

<div class="report-gallery">
  {% assign sorted_reports = site.reports | sort: "date" | reverse %}
  {% for report in sorted_reports %}
    <div class="report-card">
      <a href="{{ report.url | relative_url }}">
        <img src="{{ report.icon | relative_url }}" alt="{{ report.title }} icon" class="report-icon">
        <h3>{{ report.title }}</h3>
      </a>
    </div>
  {% endfor %}
</div>