---
layout: default
title: Blog
permalink: /blog/
---

# Blog

{% assign posts = site.posts | sort: "date" | reverse %}
{% assign current_year  = "" %}
{% assign current_month = "" %}

<div class="blog-posts">

{% for post in posts %}
{% assign y = post.date | date: "%Y" %}
{% assign m = post.date | date: "%B" %}

{%- comment -%}New year header{%- endcomment -%}
{% if y != current_year %}
{%- if current_month != "" -%}</ul>{%- assign current_month = "" -%}{% endif %}
<h2 class="year-header">{{ y }}</h2>
{% assign current_year = y %}
{% endif %}

{%- comment -%}New month header & open a fresh list{%- endcomment -%}
{% if m != current_month %}
{%- if current_month != "" -%}</ul>{% endif %}
<h3 class="month-header">{{ m }}</h3>
<ul class="month-posts">
{% assign current_month = m %}
{% endif %}

  <li>
    <div class="blog-list">
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      {% if post.tags and post.tags.size > 0 %}
        <span class="post-tags">
          {% for tag in post.tags %}
            {% assign slug = tag | strip | slugify: 'default' %}
            {% capture tag_id %}{{ slug | slice: 0,1 | upcase }}{{ slug | slice: 1, 200 }}{% endcapture %}
            <a href="{{ '/tags/#' | append: tag_id | relative_url }}" class="tag">{{ tag }}</a>
          {% endfor %}
        </span>
      {% endif %}
    </div>
  </li>
{% endfor %}

{%- if current_month != "" -%}</ul>{% endif %}

</div>
