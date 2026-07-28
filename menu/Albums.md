---
layout: page
title: Albums of the Month
---
Just some music
<div class="content-section">
  <h2 class="pinned-sticky">
    <p style="text-align: center; font-family: Palatino;">
      <span id="date-display"></span>:
      {% assign thismonth = site.time | date: "%Y-%m" %}

{% for post in site.posts %}
  {% if post.tags contains 'album' %}
    {% assign post_date = post.date | date: "%Y-%m" %}
    {% if post_date == thismonth %}
      <div class="post-content" style="text-align:center; font-size: 2.5rem; font-family: Palatino; margin-bottom: 0px">
        {{ post.title }}
      </div>
    {% endif %}
  {% endif %}
{% endfor %}
    </p>
       <div style="
    background-image: url('/imgs/Untitled15.png');
    background-repeat: repeat;
    background-size: 5%;
    width: 100%;
      height: 40px;
    border-block: 1px solid grey;"
       >
    </div>
  </h2>
<script>
  // Fetches current date and updates the text to "Month Year" format
  const dateOptions = { month: 'long', year: 'numeric' };
  const formattedDate = new Date().toLocaleDateString('en-US', dateOptions);
  document.getElementById('date-display').textContent = formattedDate;
</script>
<ul>
  {% for post in site.posts %}
    {% if post.tags contains 'album' %}
      <li>
        <h2 ><a style="color: #BB0000; letter-spacing: -1px; font-weight: 300; text-decoration: underline white;" href="{{ post.url }}">{{ post.date | date: "%B,  %Y"}} - {{ post.title }}</a>
        </h2>
        <div class="post-content;" style="font-family: Palatino">
          {{ post.content }}
        </div>
        <hr class="custom-divider;" data-darkreader-inline-border-color="grey;" data-darkreader-inline-background-color="#c7b99e">
      </li>
    {% endif %}
  {% endfor %}
</ul>
