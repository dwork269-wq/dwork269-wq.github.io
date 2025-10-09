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
      {% assign slug = tag | strip | slugify: 'default' %}
      {% capture tag_id %}{{ slug | slice: 0,1 | upcase }}{{ slug | slice: 1, 200 }}{% endcapture %}
      <a href="#{{ tag_id }}" class="tag" style="margin: 0.5rem 0.5rem 0 0; display: inline-block;">
        {{ tag | strip | capitalize }}
      </a>
    {% endif %}
  {% endfor %}
</div>

<div style="margin-top: 2rem;">
  {% for tag in sortedtags %}
    {% if tag != "" %}
      {% assign slug = tag | strip | slugify: 'default' %}
      {% capture tag_id %}{{ slug | slice: 0,1 | upcase }}{{ slug | slice: 1, 200 }}{% endcapture %}
      <div id="{{ tag_id }}" style="margin-bottom: 2rem;">
        <h2 style="margin-bottom: 1rem; padding-bottom: 0.5rem; border-bottom: 1px solid var(--muted);">
          {{ tag | strip | capitalize }}
        </h2>
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
