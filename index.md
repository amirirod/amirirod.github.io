---
layout: window
title: Primary Page
window_title: "Surprise Alert!"
window_text: "This text loads directly inside the window overlay."
---
Just some music.
<button onclick="openWindow()">Open Window</button>
<div class="content-section">
  <h2 class="sticky-text">
    <p>
      Today's date is: <span id="current-date"></span>       <div class="dropdown">
  <button class="dropbtn">Some Other Stuff</button>
  <div class="dropdown-content">
    <a class="post_navi-item nav_next" href="{{ 'albums.html' | absolute_url }}" title="Albums">Albums</a>
    <a href="#">Link 2</a>
    <a href="#">Link 3</a>
  </div>
</div>
    </p>
  </h2>

<script>
  const dateElement = document.getElementById('current-date');
  dateElement.textContent = new Date().toLocaleDateString();
</script>
<ul>
  {% for post in site.posts %}
    {% if post.tags contains 'song' %}
      <li>
        <h2><a href="{{ post.url }}">{{ post.date | date: "%B %d, %Y"}}</a>
        </h2>
        <div class="post-content">
          {{ post.content }}
        </div>
        <hr style="border: 3px solid grey; height: 7px; background-color: #82745d;">
      </li>
    {% endif %}
  {% endfor %}
</ul>
