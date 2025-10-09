---
layout: default
title: Search
permalink: /search/
---

# Search

<form action="https://duckduckgo.com/" method="get">
  <input type="hidden" name="sites" value="{{ site.url | remove: 'https://' | remove: 'http://' }}" />
  <input type="text" name="q" placeholder="Search posts…" style="width:100%;max-width:420px;padding:8px;border:1px solid var(--muted);background:var(--bg);color:var(--fg);border-radius:4px;">
  <button type="submit" style="padding:8px 16px;margin-left:8px;cursor:pointer;background:var(--link);color:var(--bg);border:none;border-radius:4px;">Search</button>
</form>
