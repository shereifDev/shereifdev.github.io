---
layout: page
permalink: /notes/
title: notes
description: My handwritten technical summaries and course notes.
nav: true
nav_order: 3
---

<div class="projects">
{% if site.notes %}
  <div class="row">
    {% for project in site.notes %}
      {% include projects.liquid %}
    {% endfor %}
  </div>
{% else %}
  <p>No notes found.</p>
{% endif %}
</div>
