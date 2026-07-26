---
layout: window
title: Primary Page
window_title: "Surprise Alert!"
window_text: "This text loads directly inside the window overlay."
---
Just some music
<button onclick="openWindow()">Open Window</button>
<ul>
  {% for post in site.posts %}
    {% if post.tags contains 'song' %}
      <li>
        <h2><a href="{{ post.url }}">{%- assign date_format = site.minima.date_format | default: "%b %-d, %Y" -%}{{ page.date | date: date_format }}</a>
        </h2>
        <div class="post-content">
          {{ post.content }}
        </div>
      </li>
    {% endif %}
  {% endfor %}
</ul>
