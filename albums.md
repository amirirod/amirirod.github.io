---
layout: page
title: Albums of the Month
---


  <ul>
    {% for post in album %}
      <li><a href="{{ post.url }}">{{ post.date | date: "%B %Y" }} - {{ post.title }}</a></li>
    {% endfor %}
  </ul>

