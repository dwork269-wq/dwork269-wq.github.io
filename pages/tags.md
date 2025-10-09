---
layout: default
title: Tags
permalink: /tags/
---

# Tags
{% assign tag_map = {} %}
{% for p in site.posts %}
  {% for t in p.tags %}
    {% if tag_map[t] %}{% assign tag_map = tag_map | merge: { t: tag_map[t] | push: p } %}
    {% else %}{% assign tag_map = tag_map | merge: { t: [p] } %}{% endif %}
  {% endfor %}
{% endfor %}

<ul>
{% for t in tag_map %}
  <li id="{{ t[0] }}"><strong>{{ t[0] }}</strong>
    <ul>
      {% for p in t[1] %}
        <li><a href="{{ p.url | relative_url }}">{{ p.title }}</a></li>
      {% endfor %}
    </ul>
  </li>
{% endfor %}
</ul>
