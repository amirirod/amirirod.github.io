---
tags: menu
title: test
---
{% assign has_new_post = false %}

{% for post in site.posts %}
{% for mark in post.mark %}
{{mark}}
{% endfor %}
{% endfor %}
