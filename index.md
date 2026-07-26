---
layout: window
title: Primary Page
window_title: "Surprise Alert!"
window_text: "This text loads directly inside the window overlay."
---
Just some music.
<button onclick="openWindow()">Open Window</button>
<ul>
  {% for song in site.tags %}
    <li>
      <h2><a href="{{ post.url }}">{{ post.date | date: "%B %Y" }} - {{ post.title }}</a></h2>
      <div class="post-content">
        {{ post.content }}
      </div>
    </li>
  {% endfor %}
</ul>

