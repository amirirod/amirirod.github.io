---
layout: page
title: Blog Archive
---
<button onmouseover= 
  <a class="post_navi-item nav_next" href="{{ 'albums.html' | absolute_url }}" title="Albums">
    Albums
  </a>
  >
</button>
{% for tag in site.tags %}
  <h3>{{ tag[0] }}</h3>
  <ul>
    {% for post in tag[1] %}
      <li><a href="{{ post.url }}">{{ post.date | date: "%B %Y" }} - {{ post.title }}</a></li>
    {% endfor %}
  </ul>
{% endfor %}
