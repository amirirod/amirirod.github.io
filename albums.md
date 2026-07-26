---
layout: page
title: Albums of the Month
---

<ul>
  {% for album in site.tags %}
    <li>
      <a href="{{ album.url }}">{{ album.date | date: "%B %Y" }} - {{ album.title }}</a>
    </li>
  {% endfor %}
</ul>
