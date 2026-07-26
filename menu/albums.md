---
layout: page
title: Albums of the Month
---
Just some music.
<div class="content-section">
  <h2 class="sticky-text">
    <p 
      style="text-align:center;
      font-family: Palatino;"
      >
      <span id="date-display"></span>:
      {% assign today = site.time | date: "%Y-%m-%d" %}

{% for post in site.posts %}
  {% if post.tags contains 'album' %}
    {% assign post_date = post.date | date: "%Y-%m-%d" %}
    {% if post_date == today %}
      <div class="post-content" style="text-align:center; font-size: 2.5rem; font-family: Palatino">
        {{ post.title }}
      </div>
    {% endif %}
  {% endif %}
{% endfor %}

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
