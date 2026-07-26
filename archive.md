---
layout: page
title: Blog Archive
---
 <a href="{{ 'albums.html' | absolute_url }}" title="Albums">
<div class="post_navi-arrow">&gt;</div><div class="post_navi-label">Albums</div><div><span>Archive of all previous blog posts</span></div>
 </a>
{% for tag in site.tags %}
  <h3>{{ tag[0] }}</h3>
  <ul>
    {% for post in tag[1] %}
      <li><a href="{{ post.url }}">{{ post.date | date: "%B %Y" }} - {{ post.title }}</a></li>
    {% endfor %}
  </ul>
{% endfor %}
