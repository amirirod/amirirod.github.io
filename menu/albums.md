---
layout: page
title: Album of the Month
---

<ul>
  {% for post in site.tags['album'] %}
    <li>
      <a href="{{ post.url }}">{{ post.date | date: "%B %Y" }} - {{ post.title }}</a>
    </li>
  {% endfor %}
</ul>
