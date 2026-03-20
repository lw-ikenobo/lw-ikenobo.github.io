---
title: "Gallery"
layout: default
---

# Gallery

Browse our exhibition photos.

{% assign items = site.pages | where_exp: "item", "item.dir contains '/Gallery/'" | where_exp: "item", "item.dir != '/Gallery/'" | sort: "dir" | reverse %}
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
