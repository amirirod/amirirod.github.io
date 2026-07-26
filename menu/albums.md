---
layout: page
title: Albums of the Month
---
<ul>
  {% for post in site.posts %}
    {% if post.tags contains 'album' %}
      <li>
        <h2><a href="{{ post.url }}">{{ post.date | date: "%B %Y"}} - {{ post.title }}</a>
        </h2>
        <div class="post-content;" style="font-family: Palatino">
          {{ post.content }}
        </div>
        <hr class="custom-divider;" data-darkreader-inline-border-color="grey;" data-darkreader-inline-background-color="#c7b99e">
      </li>
    {% endif %}
  {% endfor %}
</ul>
