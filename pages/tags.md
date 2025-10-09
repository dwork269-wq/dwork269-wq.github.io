---
layout: default
title: Tags
permalink: /tags/
---

# Tags

{% capture tags %}
{% for tag in site.tags %}
{{ tag[0] }}
{% endfor %}
{% endcapture %}
{% assign sortedtags = tags | split:' ' | sort %}

<div class="tags-list">
  {% for tag in sortedtags %}
    {% if tag != "" %}
      <a href="#{{ tag | slugify }}" class="tag" style="margin: 0.5rem 0.5rem 0 0; display: inline-block;">{{ tag }}</a>
    {% endif %}
  {% endfor %}
</div>

<div style="margin-top: 2rem;">
  {% for tag in sortedtags %}
    {% if tag != "" %}
      <div id="{{ tag | slugify }}" style="margin-bottom: 2rem;">
        <h2 style="margin-bottom: 1rem; padding-bottom: 0.5rem; border-bottom: 1px solid var(--muted);">{{ tag }}</h2>
        <ul class="post-list">
          {% for post in site.tags[tag] %}
            <li>
              <span class="post-date">{{ post.date | date: "%b %-d, %Y" }}</span>
              <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
            </li>
          {% endfor %}
        </ul>
      </div>
    {% endif %}
  {% endfor %}
</div>
