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
    <p 
      style="text-align:center;
      font-family: Palatino;"
      >
      <span id="date-display"></span>:
      {% assign today = site.time | date: "%Y-%m-%d" %}

{% for post in site.posts %}
  {% if post.tags contains 'song' %}
    {% assign post_date = post.date | date: "%Y-%m-%d" %}
    {% if post_date == today %}
      <div class="post-content" style="text-align:center; font-size: 2.5rem; font-family: Palatino">
        {{ post.title }}
      </div>
    {% endif %}
  {% endif %}
{% endfor %}
  <div class="dropdown">
  <button class="dropbtn">Some Other Stuff</button>
  <div class="dropdown-content">
    <a class="post_navi-item nav_next" href="{{ 'menu/albums.html' | absolute_url }}" title="Albums">Albums</a>
    <a href="#">Link 2</a>
    <a href="#">Link 3</a>
  </div>
</div>
    </p>
    <hr style="background-color: white">
  </h2>
 <script>
        // Get the current date
        const today = new Date();
        
        // Define options for MMMM DD, YYYY format
        const options = { year: 'numeric', month: 'long', day: '2-digit' };
        
        // Format the date using the browser's language setting
        const formattedDate = today.toLocaleDateString('en-US', options);
        
        // Insert the formatted date into the HTML span
        document.getElementById('date-display').textContent = formattedDate;
    </script>
<ul>
  {% for post in site.posts %}
    {% if post.tags contains 'song' %}
      <li>
        <h2 ><a style="color: #BB0000; letter-spacing: -1px; font-weight: 320; text-decoration: underline white;" href="{{ post.url }}">{{ post.date | date: "%B %d, %Y"}} - {{ post.title }}</a>
        </h2>
        <div class="post-content;" style="font-family: Palatino">
          {{ post.content }}
        </div>
        <hr class="custom-divider;" data-darkreader-inline-border-color="grey;" data-darkreader-inline-background-color="#c7b99e">
      </li>
    {% endif %}
  {% endfor %}
</ul>
