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

<div id="searchResults" style="display: none;">
  <h2>Search Results</h2>
  <div id="resultsList"></div>
  <p><a href="#" onclick="clearSearch()" style="color: var(--link);">← Back to all posts</a></p>
</div>

<div id="allPosts">
  <h2>All Posts</h2>
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
      <h3 class="year-header">{{ post_year }}</h3>
      <ul class="post-list">
      {% assign current_year = post_year %}
      {% assign current_month = "" %}
    {% endif %}
    
    {% if current_month != post_month %}
      {% if current_month != "" %}
        </ul>
      {% endif %}
      <h4 class="month-header">{{ post_month }}</h4>
      <ul class="month-posts">
      {% assign current_month = post_month %}
    {% endif %}
    
    <li data-title="{{ post.title | downcase }}" data-content="{{ post.content | strip_html | downcase }}" data-tags="{{ post.tags | join: ' ' | downcase }}">
      <span class="post-date">{{ post.date | date: "%-d" }}</span>
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      {% if post.tags and post.tags.size > 0 %}
        <span class="post-tags">
          {% for tag in post.tags %}
            <a href="{{ '/tags/#' | append: tag | slugify | relative_url }}" class="tag">{{ tag }}</a>
          {% endfor %}
        </span>
      {% endif %}
    </li>
  {% endfor %}
    </ul>
  </ul>
  </div>
</div>

<script>
function searchPosts(event) {
  event.preventDefault();
  const query = document.getElementById('searchInput').value.toLowerCase().trim();
  
  if (!query) {
    clearSearch();
    return;
  }
  
  const allPosts = document.querySelectorAll('#allPosts .month-posts li');
  const results = [];
  
  allPosts.forEach(post => {
    const title = post.getAttribute('data-title');
    const content = post.getAttribute('data-content');
    const tags = post.getAttribute('data-tags');
    
    if (title.includes(query) || content.includes(query) || tags.includes(query)) {
      results.push(post.cloneNode(true));
    }
  });
  
  if (results.length > 0) {
    displayResults(results, query);
  } else {
    displayNoResults(query);
  }
}

function displayResults(results, query) {
  const resultsList = document.getElementById('resultsList');
  const searchResults = document.getElementById('searchResults');
  const allPosts = document.getElementById('allPosts');
  
  if (results.length === 0) {
    displayNoResults(query);
    return;
  }
  
  // Group results by year and month
  const groupedResults = {};
  results.forEach(result => {
    const dateText = result.querySelector('.post-date').textContent;
    const link = result.querySelector('a');
    const title = link.textContent;
    const url = link.href;
    const tags = result.querySelector('.post-tags');
    const tagText = tags ? tags.textContent : '';
    
    // Create a date object from the day number (we need to get the full date)
    const postElement = result;
    const dataTitle = postElement.getAttribute('data-title');
    const dataContent = postElement.getAttribute('data-content');
    const dataTags = postElement.getAttribute('data-tags');
    
    // For now, just display results in a simple list
    const resultItem = result.cloneNode(true);
    resultsList.appendChild(resultItem);
  });
  
  searchResults.style.display = 'block';
  allPosts.style.display = 'none';
  
  // Highlight search terms
  highlightSearchTerms(query);
}

function displayNoResults(query) {
  const resultsList = document.getElementById('resultsList');
  resultsList.innerHTML = `<p style="color: var(--muted);">No posts found for "${query}"</p>`;
  
  document.getElementById('searchResults').style.display = 'block';
  document.getElementById('allPosts').style.display = 'none';
}

function clearSearch() {
  document.getElementById('searchInput').value = '';
  document.getElementById('searchResults').style.display = 'none';
  document.getElementById('allPosts').style.display = 'block';
}

function highlightSearchTerms(query) {
  const terms = query.split(' ').filter(term => term.length > 0);
  const results = document.querySelectorAll('#resultsList a');
  
  results.forEach(link => {
    let html = link.innerHTML;
    terms.forEach(term => {
      const regex = new RegExp(`(${term})`, 'gi');
      html = html.replace(regex, '<mark style="background: rgba(88, 166, 255, 0.3); padding: 0.1em 0.2em; border-radius: 2px;">$1</mark>');
    });
    link.innerHTML = html;
  });
}

// Handle URL parameters for direct search links
window.addEventListener('load', function() {
  const urlParams = new URLSearchParams(window.location.search);
  const query = urlParams.get('q');
  if (query) {
    document.getElementById('searchInput').value = query;
    searchPosts({ preventDefault: () => {} });
  }
});
</script>
