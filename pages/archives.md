---
layout: default
title: Archive
permalink: /archives/
---

# Archive

{% assign years = site.posts | group_by_exp:"post","post.date | date: '%Y'" %}
{% for y in years %}
## {{ y.name }}
  {% assign months = y.items | group_by_exp:"post","post.date | date: '%B'" %}
  {% for m in months %}
### {{ m.name }}
  {% for p in m.items %}
- <a href="{{ p.url | relative_url }}">{{ p.title }}</a>
  {% endfor %}
  {% endfor %}
{% endfor %}
