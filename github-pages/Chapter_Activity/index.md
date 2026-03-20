---
title: "Chapter Activity"
layout: default
---

# Chapter Activities

Please enjoy the photos of our Chapter activities.

{% assign items = site.pages | where_exp: "item", "item.dir contains '/Chapter_Activity/'" | where_exp: "item", "item.dir != '/Chapter_Activity/'" | sort: "dir" | reverse %}
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
