---
layout: page
title: Artists of the Week
---
Just some music.
<div class="content-section">
  <h2 class="pinned-sticky">
    <p style="text-align: center; font-family: Palatino;">
      <span id="date-display"></span>:
      {% assign thisweek = site.time | date: "%Y-%V" %}

{% for post in site.posts %}
  {% if post.tags contains 'Artists' %}
    {% assign post_date = post.date | date: "%Y-%V" %}
    {% if post_date == thisweek %}
      <div class="post-content" style="text-align:center; font-size: 2.5rem; font-family: Palatino">
        {{ post.title }}
      </div>
    {% endif %}
  {% endif %}
{% endfor %}
    </p>
       <div style="
    background-image: url('imgs/Untitled15.png');
    background-repeat: repeat;
    background-size: 5%;
    width: 100%;
      height: 40px;
    border-block: 1px solid grey;"
       >
    </div>
  </h2>
<script>
  // Fetches the current ISO week number and year for the headline
  const today = new Date();
  
  // Calculate the current ISO week number (Matches Liquid's %V)
  const target = new Date(today.valueOf());
  const dayNr = (today.getDay() + 6) % 7;
  target.setDate(target.getDate() - dayNr + 3);
  const firstThursday = target.valueOf();
  target.setMonth(0, 1);
  if (target.getDay() !== 4) {
    target.setMonth(0, 1 + ((4 - target.getDay()) + 7) % 7);
  }
  const weekNumber = 1 + Math.ceil((firstThursday - target) / 604800000);
  
  document.getElementById('date-display').textContent = `Week ${weekNumber}, ${today.getFullYear()}`;
</script>
<ul>
  {% for post in site.posts %}
    {% if post.tags contains 'Artists' %}
      <li>
        <h2>
          <a style="color: #BB0000; letter-spacing: -1px; font-weight: 300; text-decoration: underline white;" href="{{ post.url }}">Week {{ post.date | date: "%V, %Y"}} - {{ post.title }}</a>
        </h2>
        <div class="post-content" style="font-family: Palatino">
          {{ post.content }}
        </div>
        <hr class="custom-divider" style="border-color: grey; background-color: #c7b99e;">
      </li>
    {% endif %}
  {% endfor %}
</ul>

