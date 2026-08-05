---
tags: menu
title: test
---
{% for post in site.posts %}
  {% assign current_time = 'now' | date: '%s' | plus: 0 %}
  {% assign post_time = post.date | date: '%s' | plus: 0 %}
  {% assign diff_seconds = current_time | minus: post_time %}
  {% assign diff_days = diff_seconds | divided_by: 3600 | divided_by: 24 %}
  
  {% if diff_days <= 7 %}
    <span class="new-badge">New!</span>
  {% endif %}
{% endfor %}
