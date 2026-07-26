---
layout: page
title: Albums of the Month
---

{% for album in site.tags %}

  <h3>{{ album }}</h3>
  <ul>
    {% for post in album %}
      <li><a href="{{ post.url }}">{{ post.date | date: "%B %Y" }} - {{ post.title }}</a></li>
    {% endfor %}
  </ul>

{% endfor %}
