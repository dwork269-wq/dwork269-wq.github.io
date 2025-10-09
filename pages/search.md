---
layout: default
title: Search
permalink: /search/
---

# Search

<div style="margin-bottom: 2rem;">
  <form action="https://duckduckgo.com/" method="get" target="_blank" class="search-form">
    <input type="hidden" name="sites" value="{{ site.url | remove: 'https://' | remove: 'http://' }}" />
    <input type="text" name="q" placeholder="Search posts…" />
    <button type="submit">Search with DuckDuckGo</button>
  </form>
  <p style="color: var(--muted); font-size: 0.9em; margin-top: 0.5rem;">
    Opens in new tab • Searches only this site
  </p>
</div>

## All Posts

<ul class="post-list">
{% for post in site.posts %}
  <li>
    <span class="post-date">{{ post.date | date: "%b %-d, %Y" }}</span>
    <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
    {% if post.tags and post.tags.size > 0 %}
      <span style="color: var(--muted); font-size: 0.85em;">
        {% for tag in post.tags %}
          <span style="background: var(--muted); color: var(--bg); padding: 0.2em 0.4em; border-radius: 3px; margin-left: 0.3em; font-size: 0.8em;">{{ tag }}</span>
        {% endfor %}
      </span>
    {% endif %}
  </li>
{% endfor %}
</ul>
