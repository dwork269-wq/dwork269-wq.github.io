---
layout: default
title: Blog
permalink: /blog/
---

# Blog

<div class="blog-posts">
{% assign current_year = "" %}
{% assign current_month = "" %}
{% for post in site.posts %}
  {% assign post_year = post.date | date: "%Y" %}
  {% assign post_month = post.date | date: "%B" %}
  
  {% if current_year != post_year %}
    {% if current_year != "" %}
      </ul>
    {% endif %}
    <h2 class="year-header">{{ post_year }}</h2>
    <ul class="post-list">
    {% assign current_year = post_year %}
    {% assign current_month = "" %}
  {% endif %}
  
  {% if current_month != post_month %}
    {% if current_month != "" %}
      </ul>
    {% endif %}
    <h3 class="month-header">{{ post_month }}</h3>
    <ul class="month-posts">
    {% assign current_month = post_month %}
  {% endif %}
  
  <li>
    <span class="post-date">{{ post.date | date: "%-d" }}</span>
    <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
    {% if post.tags and post.tags.size > 0 %}
      <span class="post-tags">
        {% for tag in post.tags %}
          {% assign tag_id = tag | strip | downcase | slugify: 'default' %}
          <a href="{{ '/tags/#' | append: tag_id | relative_url }}" class="tag">{{ tag }}</a>
        {% endfor %}
      </span>
    {% endif %}
  </li>
{% endfor %}
  </ul>
</ul>
</div>
