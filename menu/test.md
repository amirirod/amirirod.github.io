---
tags: menu
title: test
---
{% for posts in site.posts %}
{% assign diff_seconds = 'now' | date: '%s' | minus: post.date | date: '%s' %}
{% assign diff_days = diff_seconds | divided_by: 3600 | divided_by: 24 %}
{% if diff_days <= 7 %}
  <span class="new-badge">New!</span>
{% endif %}
{% endfor %}
