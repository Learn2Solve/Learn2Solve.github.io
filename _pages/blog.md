---
layout: page
title: Blog
permalink: /blog/
description: My thoughts and experiences in AI, Finance, and Technology.
nav: true
nav_order: 2

pagination:
  enabled: true
  collection: posts
  permalink: /page/:num/
  per_page: 5
  sort_field: date
  sort_reverse: true
  trail: 
    before: 1
    after: 1
---

<div class="post-list">
  {% if page.pagination.enabled %}
    {% assign postlist = paginator.posts %}
  {% else %}
    {% assign postlist = site.posts %}
  {% endif %}

  {% for post in postlist %}
  <div class="post-preview">
    <div class="post-meta">
      <div class="post-date">{{ post.date | date: "%B %-d, %Y" }}</div>
    </div>

    <div class="post-title">
      {% if post.redirect == blank %}
        <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      {% elsif post.redirect contains '://' %}
        <a href="{{ post.redirect }}" target="_blank">{{ post.title }}</a>
        <svg width="2rem" height="2rem" viewBox="0 0 40 40" xmlns="http://www.w3.org/2000/svg">
          <path d="M17 13.5v6H5v-12h6m3-3h6v6m0-6-9 9" class="icon_svg-stroke" stroke="#999" stroke-width="1.5" fill="none" fill-rule="evenodd" stroke-linecap="round" stroke-linejoin="round"></path>
        </svg>
      {% else %}
        <a href="{{ post.redirect | relative_url }}">{{ post.title }}</a>
      {% endif %}
    </div>

    <div class="post-description">
      {{ post.description }}
    </div>
  </div>
  {% endfor %}
</div>

{% if paginator.total_pages > 1 %}
<div class="pagination">
  {% include pagination.liquid %}
</div>
{% endif %}
