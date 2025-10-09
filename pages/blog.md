---
layout: default
title: Blog
permalink: /blog/
---

# Blog

<ul class="post-list">
  {% assign posts_by_date = site.posts | sort: "date" | reverse %}
  {% for post in posts_by_date %}
    <li>
      <time class="post-date">{{ post.date | date: "%Y-%m-%d" }}</time>
      <a class="post-link" href="{{ post.url | relative_url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>

<p><a href="{{ '/archives/' | relative_url }}">Browse the Archives →</a></p>
