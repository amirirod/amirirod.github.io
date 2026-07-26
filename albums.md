---
layout: page
title: Albums of the Month
---

{% for album in site.tags %}
  <ul>
      <li><a href="{{ post.url }}">{{ post.date | date: "%B %Y" }} - {{ post.title }}</a></li>
  </ul>
{% endfor %}
