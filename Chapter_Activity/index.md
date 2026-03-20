---
title: "Chapter Activity"
layout: default
---

# Chapter Activities

Please enjoy the photos of our Chapter activities.

{% assign items = site.pages | where_exp: "item", "item.dir contains '/Chapter_Activity/'" | where_exp: "item", "item.dir != '/Chapter_Activity/'" | sort: "dir" | reverse %}
<div class="gallery-grid">
{% for p in items %}
  {% assign thumb = nil %}
  {% for f in site.static_files %}
    {% if f.path contains p.dir and f.extname == '.jpg' %}
      {% assign thumb = f.path | relative_url %}
      {% break %}
    {% endif %}
  {% endfor %}
  <a class="gallery-tile" href="{{ p.url }}"{% if thumb %} style="background-image: url('{{ thumb }}')"{% endif %}>
    <span>{{ p.title }}</span>
  </a>
{% endfor %}
</div>
