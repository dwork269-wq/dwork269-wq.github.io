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

<div class="tag-filter-section">
  <button class="tag-filter-toggle" id="tagFilterToggle" onclick="toggleTagFilter()">
    <span>🏷️ Filter by Tag</span>
    <span class="toggle-arrow">▼</span>
  </button>
  <div class="tag-filter-dropdown" id="tagFilterDropdown" style="display: none;">
    <div class="tag-filter-actions">
      <button class="filter-action-btn" onclick="selectAllTags()">Select All</button>
      <button class="filter-action-btn" onclick="clearAllTags()">Clear All</button>
      <button class="filter-action-btn filter-apply-btn" onclick="applyTagFilter()">Apply Filter</button>
    </div>
    <div class="tag-filter-list" id="tagFilterList">
      {% assign all_tags = site.posts | map: 'tags' | join: ',' | split: ',' | uniq | sort %}
      {% for tag in all_tags %}
        {% if tag != '' %}
          <label class="tag-filter-item">
            <input type="checkbox" value="{{ tag | strip | downcase }}" />
            <span class="tag-filter-label">{{ tag | strip }}</span>
          </label>
        {% endif %}
      {% endfor %}
    </div>
  </div>
</div>

<div id="emptyState" style="text-align: center; padding: 3rem 1rem; color: var(--muted);">
  <p style="font-size: 1.1em; margin-bottom: 0.5rem;">🔍 Start typing to search posts</p>
  <p style="font-size: 0.9em;">Search by title, content, or tags</p>
</div>

<div id="searchResults" style="display:none;">
  <h2>Search Results</h2>
  <div id="resultsList"></div>
  <p><a href="#" onclick="clearSearch()" style="color: var(--link);">← Clear search</a></p>
</div>

<div id="allPosts" style="display:none;">

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
let selectedTags = [];

function toggleTagFilter() {
  const dropdown = document.getElementById('tagFilterDropdown');
  const arrow = document.querySelector('.toggle-arrow');
  const isHidden = dropdown.style.display === 'none';
  dropdown.style.display = isHidden ? 'block' : 'none';
  arrow.textContent = isHidden ? '▲' : '▼';
}

function selectAllTags() {
  document.querySelectorAll('.tag-filter-item input[type="checkbox"]').forEach(cb => {
    cb.checked = true;
  });
}

function clearAllTags() {
  document.querySelectorAll('.tag-filter-item input[type="checkbox"]').forEach(cb => {
    cb.checked = false;
  });
  selectedTags = [];
  applyTagFilter();
}

function applyTagFilter() {
  const checkboxes = document.querySelectorAll('.tag-filter-item input[type="checkbox"]:checked');
  selectedTags = Array.from(checkboxes).map(cb => cb.value);
  
  if (selectedTags.length === 0) {
    // If no tags selected, show empty state
    document.getElementById('emptyState').style.display = 'block';
    document.getElementById('searchResults').style.display = 'none';
    document.getElementById('searchInput').value = '';
  } else {
    // Perform search with selected tags
    performSearch('');
  }
  
  // Close dropdown after applying
  toggleTagFilter();
}

function performSearch(q) {
  const nodes = document.querySelectorAll('#allPosts .month-posts li');
  const results = [];
  
  nodes.forEach(li => {
    const title = li.getAttribute('data-title') || '';
    const content = li.getAttribute('data-content') || '';
    const tags = li.getAttribute('data-tags') || '';
    
    // Check text search
    const matchesText = !q || title.includes(q) || content.includes(q) || tags.includes(q);
    
    // Check tag filter
    const matchesTags = selectedTags.length === 0 || 
                        selectedTags.some(tag => tags.includes(tag));
    
    if (matchesText && matchesTags) {
      results.push(li.cloneNode(true));
    }
  });

  const wrap = document.getElementById('resultsList');
  wrap.innerHTML = '';
  
  if(results.length === 0){
    const message = q ? `No posts found for "${q}"` : 'No posts found with selected tags';
    wrap.innerHTML = `<p style="color: var(--muted);">${message}</p>`;
  } else {
    const ul = document.createElement('ul');
    ul.className = 'month-posts';
    results.forEach(r => {
      r.style.display = '';
      ul.appendChild(r);
    });
    wrap.appendChild(ul);
  }

  document.getElementById('emptyState').style.display = 'none';
  document.getElementById('searchResults').style.display = 'block';
  
}

function searchPosts(event){
  event.preventDefault();
  const q = document.getElementById('searchInput').value.toLowerCase().trim();
  if(!q && selectedTags.length === 0){ 
    clearSearch();
    return;
  }
  performSearch(q);
}

function clearSearch(){
  document.getElementById('searchInput').value = '';
  document.getElementById('searchResults').style.display = 'none';
  document.getElementById('emptyState').style.display = 'block';
  // Reset tag filter
  selectedTags = [];
  document.querySelectorAll('.tag-filter-item input[type="checkbox"]').forEach(cb => {
    cb.checked = false;
  });
}

// support /search/?q=...
window.addEventListener('load', () => {
  const q = new URLSearchParams(window.location.search).get('q');
  if(q){ 
    document.getElementById('searchInput').value = q; 
    performSearch(q);
  }
});
</script>
