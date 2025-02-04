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
  {% for post in paginator.posts %}
  <div class="post-preview">
    <div class="post-meta">
      <div class="post-date">{{ post.date | date: "%B %-d, %Y" }}</div>
    </div>

    <div class="post-title">
      <a href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a>
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
