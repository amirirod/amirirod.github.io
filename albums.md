---
layout: page
title: Albums of the Month
---

{% for post in album %}
  <ul>
      <li><a href="{{ post.url }}">{{ post.date | date: "%B %Y" }} - {{ post.title }}</a></li>
  </ul>
{% endfor %}
