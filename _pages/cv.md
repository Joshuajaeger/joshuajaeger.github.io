---
layout: page
title: CV
permalink: /cv/
description: A brief overview of my academic background.
nav: true
nav_order: 4
---

{% for entry in site.data.cv %}

<div class="cv-section">
<h2>{{ entry.title }}</h2>

{% if entry.type == "map" %}
<ul>
{% for item in entry.contents %}
  <li><strong>{{ item.name }}</strong>: {{ item.value }}</li>
{% endfor %}
</ul>

{% elsif entry.type == "time_table" %}
{% for item in entry.contents %}
<div class="cv-entry" style="margin-bottom: 1.5rem;">
  <div style="display: flex; justify-content: space-between; align-items: baseline;">
    <h4 style="margin-bottom: 0.25rem;">{{ item.title }}</h4>
    <span class="text-muted" style="white-space: nowrap; margin-left: 1rem;">{{ item.year }}</span>
  </div>
  {% if item.institution %}
  <p class="text-muted" style="margin-bottom: 0.25rem;">{{ item.institution }}</p>
  {% endif %}
  {% if item.description %}
  <ul>
    {% for desc in item.description %}
    <li>{{ desc }}</li>
    {% endfor %}
  </ul>
  {% endif %}
</div>
{% endfor %}

{% elsif entry.type == "list" %}
<ul>
{% for item in entry.contents %}
  <li>{{ item }}</li>
{% endfor %}
</ul>
{% endif %}

</div>

{% endfor %}
