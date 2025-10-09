---
layout: default
title: Archive
permalink: /archives/
---

# Archive

<div class="archive-grid">
{% assign years = site.posts | group_by_exp:"post","post.date | date: '%Y'" %}
{% for y in years %}
  {% assign months = y.items | group_by_exp:"post","post.date | date: '%B'" %}
  {% for m in months %}
    <div class="year">{% if forloop.first %}{{ y.name }}{% endif %}</div>
    <div class="month">{{ m.name }}</div>
    <ul class="entries">
      {% for p in m.items %}
        <li><a href="{{ p.url | relative_url }}">{{ p.title }}</a></li>
      {% endfor %}
    </ul>
  {% endfor %}
{% endfor %}
</div>
