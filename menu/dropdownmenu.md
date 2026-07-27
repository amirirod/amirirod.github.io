---
layout: page
title: Albums of the Month
---
Just some music.
<div class="content-section">
  <h2 class="pinned-sticky">
    <p style="text-align: center; font-family: Palatino;">
      <span id="date-display"></span>:
      {% assign thisweek = site.time | date: "%Y-%m-%W" %}

{% for post in site.posts %}
  {% if post.tags contains 'Artists' %}
    {% assign post_date = post.date | date: "%Y-%m-W" %}
    {% if post_date == thisweek %}
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
  // Fetches current date and updates the text to "Month Year" format
  const dateOptions = { month: 'long', year: 'numeric' };
  const formattedDate = new Date().toLocaleDateString('en-US', dateOptions);
  document.getElementById('date-display').textContent = formattedDate;
</script>
<ul>
  {% for post in site.posts %}
    {% if post.tags contains 'Artists' %}
      <li>
        <h2 ><a style="color: #BB0000; letter-spacing: -1px; font-weight: 320; text-decoration: underline white;" href="{{ post.url }}">{{ post.date | date: "%B %W, %Y"}} - {{ post.title }}</a>
        </h2>
        <div class="post-content;" style="font-family: Palatino">
          {{ post.content }}
        </div>
        <hr class="custom-divider;" data-darkreader-inline-border-color="grey;" data-darkreader-inline-background-color="#c7b99e">
      </li>
    {% endif %}
  {% endfor %}
</ul>
</style>



