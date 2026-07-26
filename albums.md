---
layout: page
title: Albums of the Month
---

{% for tag in site.tags %}
{% for album in tag %}
  <h3>{{ tag[0] }}</h3>
  <ul>
    {% for post in album %}
      <li><a href="{{ post.url }}">{{ post.date | date: "%B %Y" }} - {{ post.title }}</a></li>
    {% endfor %}
  </ul>
{% endfor %}
{% endfor %}
