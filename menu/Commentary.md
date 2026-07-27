---
layout: page
title: Commentary
window_title: "Surprise Alert!"
window_text: "This text loads directly inside the window overlay."
---
Just some music.
<div class="content-section">
  <h2 class="pinned-sticky">
    <p style="text-align: center; font-family: Palatino;">
      <span id="date-display"></span>:
      {% assign today = site.time | date: "%Y-%m-%d" %}

{% for post in site.posts %}
  {% if post.tags contains 'commentary' %}
    {% assign post_date = post.date | date: "%Y-%m-%d" %}
    {% if post_date == today %}
      <div class="post-content" style="text-align:center; font-size: 2.5rem; font-family: Palatino">
        {{ post.title }}
      </div>
      {% else %}
      <div style="text-align:center; font-size: 2.5rem; font-family: Palatino">
        Nothing to say today.
      </div>
    {% endif %}
  {% endif %}
{% endfor %}
    </p>
    <hr style="background-color: white">
  </h2>
 <script>
        const today = new Date();
const options = { year: 'numeric', month: 'long', day: 'numeric' };
const formattedDate = today.toLocaleDateString(undefined, options); 
document.getElementById('date-display').textContent = formattedDate;
    </script>
<ul>
  {% for post in site.posts %}
    {% if post.tags contains 'commentary' %}
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
