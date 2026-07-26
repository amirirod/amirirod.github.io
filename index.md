---
layout: window
title: Primary Page
window_title: "Surprise Alert!"
window_text: "This text loads directly inside the window overlay."
---
Just some music.
<button onclick="openWindow()">Open Window</button>
<ul>
  {% for post in site.posts %}
    {% if post.tags contains 'song' %}
      <li>
        <h2><a href="{{ post.url }}">{{ post.date | date: "%B %d, %Y"}}</a>
        </h2>
        <div class="post-content">
          {{ post.content }}
        </div>
        <hr style="border: grey; height: 7px; background-color: #C7B99E;">
      </li>
    {% endif %}
  {% endfor %}
</ul>
