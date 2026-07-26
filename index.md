---
layout: window
title: Primary Page
window_title: "Surprise Alert!"
window_text: "This text loads directly inside the window overlay."
---
Just some music.
<button onclick="openWindow()">Open Window</button>
<ul>
  {% for post in site.tags %}
    <li>
      <iframe src="{{ post.url }}" width="100%" height="300px" frameborder="0"></iframe>
    </li>
  {% endfor %}
</ul>

