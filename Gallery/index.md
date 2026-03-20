---
title: "Gallery"
layout: default
---

# Gallery

Browse our exhibition photos.

{% assign items = site.pages | where_exp: "item", "item.dir contains '/Gallery/'" | where_exp: "item", "item.dir != '/Gallery/'" | sort: "dir" | reverse %}
<ul class="page-list">
{% for p in items %}
  <li>
    <a href="{{ p.url }}">{{ p.title }}</a>
    {% for f in site.static_files %}
      {% if f.path contains p.dir and f.extname == '.jpg' %}
    <br><a href="{{ p.url }}"><img src="{{ f.path | relative_url }}" alt="{{ p.title }}"></a>
        {% break %}
      {% endif %}
    {% endfor %}
  </li>
{% endfor %}
</ul>
