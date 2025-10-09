---
layout: default
title: Search
permalink: /search/
---

# Search

<div style="margin-bottom: 2rem;">
  <form class="search-form" onsubmit="searchPosts(event)">
    <input type="text" id="searchInput" placeholder="Search posts…" />
    <button type="submit">Search</button>
  </form>
  <p style="color: var(--muted); font-size: 0.9em; margin-top: 0.5rem;">
    Search through all posts instantly
  </p>
</div>

<div id="searchResults" style="display:none;">
  <h2>Search Results</h2>
  <div id="resultsList"></div>
  <p><a href="#" onclick="clearSearch()" style="color: var(--link);">← Back to all posts</a></p>
</div>

<div id="allPosts">
  <h2>All Posts</h2>

  {% assign posts = site.posts | sort: "date" | reverse %}
  {% assign current_year  = "" %}
  {% assign current_month = "" %}

  <div class="blog-posts">
  {% for post in posts %}
    {% assign y = post.date | date: "%Y" %}
    {% assign m = post.date | date: "%B" %}

    {% if y != current_year %}
      {%- if current_month != "" -%}</ul>{%- assign current_month = "" -%}{% endif %}
      <h3 class="year-header">{{ y }}</h3>
      {% assign current_year = y %}
    {% endif %}

    {% if m != current_month %}
      {%- if current_month != "" -%}</ul>{% endif %}
      <h4 class="month-header">{{ m }}</h4>
      <ul class="month-posts">
      {% assign current_month = m %}
    {% endif %}

    <li
      data-title="{{ post.title | downcase }}"
      data-content="{{ post.content | strip_html | downcase }}"
      data-tags="{{ post.tags | join: ' ' | downcase }}"
    >
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
  {%- if current_month != "" -%}</ul>{% endif %}
  </div>
</div>

<script>
function searchPosts(event){
  event.preventDefault();
  const q = document.getElementById('searchInput').value.toLowerCase().trim();
  if(!q){ return clearSearch(); }

  const nodes = document.querySelectorAll('#allPosts .month-posts li');
  const results = [];
  nodes.forEach(li => {
    const title = li.getAttribute('data-title') || '';
    const content = li.getAttribute('data-content') || '';
    const tags = li.getAttribute('data-tags') || '';
    if (title.includes(q) || content.includes(q) || tags.includes(q)) {
      results.push(li.cloneNode(true));
    }
  });

  const wrap = document.getElementById('resultsList');
  wrap.innerHTML = '';
  if(results.length === 0){
    wrap.innerHTML = `<p style="color: var(--muted);">No posts found for "${q}"</p>`;
  } else {
    results.forEach(r => wrap.appendChild(r));
  }

  document.getElementById('searchResults').style.display = 'block';
  document.getElementById('allPosts').style.display = 'none';
  highlightSearchTerms(q);
}

function clearSearch(){
  document.getElementById('searchInput').value = '';
  document.getElementById('searchResults').style.display = 'none';
  document.getElementById('allPosts').style.display = 'block';
}

function highlightSearchTerms(q){
  const terms = q.split(' ').filter(Boolean);
  const links = document.querySelectorAll('#resultsList a');
  links.forEach(a => {
    let html = a.innerHTML;
    terms.forEach(t => html = html.replace(new RegExp(`(${t})`,'gi'),
      '<mark style="background: rgba(88,166,255,.3); padding:.1em .2em; border-radius:2px;">$1</mark>'));
    a.innerHTML = html;
  });
}

// support /search/?q=...
window.addEventListener('load', () => {
  const q = new URLSearchParams(window.location.search).get('q');
  if(q){ document.getElementById('searchInput').value = q; searchPosts({preventDefault:()=>{}}); }
});
</script>
