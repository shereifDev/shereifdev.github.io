---
layout: page
permalink: /notes/
title: notes
description: My handwritten technical summaries and course notes.
nav: true
nav_order: 3
---

<div class="projects">
{% if site.notes != blank %}
  <div class="grid">
    {% for project in site.notes %}
      {% include projects.liquid project=project %}
    {% endfor %}
  </div>
{% else %}
  <p>No notes found.</p>
{% endif %}
</div>
