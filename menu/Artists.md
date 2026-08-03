---
layout: window
title: Artists of the Week
window_title: "About Me"
window_text: "This text loads directly inside the window overlay."
tags: menu
---
<!--
<div class="content-section">
  <h2 class="pinned-sticky">
    <p style="text-align: center; font-family: Palatino;">
      <span id="date-display"></span>:
      {% assign thisweek = site.time | date: "%Y-%V" %}

{% for post in site.posts %}
  {% if post.tags contains 'Artists' %}
    {% assign post_date = post.date | date: "%Y-%V" %}
    {% if post_date == thisweek %}
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
-->
 <div style="font-size: 1.5rem; width: 100%; text-align: center; font-family: Palatino;"><span id="date-display" style=" padding: 10px 0px"></span>:</div>


<div>
<div class="content-section" style="background: black; z-index:1">
  <div style="position: sticky; top: 90px; background: black; z-index: 5">
    <p style="text-align: center; font-family: Palatino;">
      <hr>
      <div style="text-align: center; font-family: Palatino;">
       <span id="date-display" style="padding: 10px 0px"></span> 
      </div>
      {% assign thisweek = site.time | date: "%Y-%V" %}

{% for post in site.posts %}
  {% if post.tags contains 'artist' %}
    {% assign post_date = post.date | date: "%Y-%V" %}
    {% if post_date == thisweek %}
      <div class="post-content" style="text-align:center; font-size: 2.5rem; font-family: Palatino; margin-bottom: 0px">
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
    position: relative;
    z-index: 100;
    width: 100%;
    height: 40px;
    border-block: 1px solid grey;"
    >
    </div>
    

 
  </div>
  

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
    {% if post.tags contains 'artist' %}
      <li>
        <h2>
          <a class="shrink-btn" onclick="this.parentElement.parentElement.classList.toggle('active');" style="color: #BB0000; letter-spacing: -1px; font-weight: 300; text-decoration: underline white;" href="{{ post.url }}">
            Week {{ post.date | date: "%V, %Y"}} - {{ post.title }}
          </a>
        </h2>
        <div class="post-content" style="font-family: Palatino;">
          <!-- Enclosing the text string prevents it from merging into the iframe markup -->
          <p style="margin-bottom: 10px;">
            {{ post.blurb_text | truncatewords: 40 }}
          </p>
          TLDR: <u>{{ post.tldr }}</u><br><br>
          <div style="display: flex; align-items: center; justify-content: center; width: 100%; height: 180px; background-image: url('/imgs/Back.png'); box-sizing: border-box; padding: 10px">
           <video id="vid" autoplay muted loop playsinline 
           style="position: absolute; width: 100px; height: 100px; object-fit: contain; z-index: 1; pointer-events: none;">
        <source id="source" src="/imgs/LoaderTQ-1.mov" type="video/QuickTime" style="background: transparent !important">
    </video>
    <iframe 
      class="dynamic-music-embed" 
      data-testid="embed-iframe" 
      style="border-radius: 12px; margin-top: 20px !important; border: none; min-height: 152px !important; max-height: 250px !important; width: 100% !important; height: 180px !important; z-index: 3" 
      data-spotify="{{ post.spotify_link }}"
      data-apple="{{ post.apple_link }}"
      allowfullscreen="" 
      allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" 
      loading="lazy"></iframe>
</div>
        </div>
        <hr>
      </li>
    {% endif %}
  {% endfor %}
</ul>

<script>
document.addEventListener("DOMContentLoaded", function () {
  // Read whatever preference was set (either on this page or the settings page)
  let savedPlatform = localStorage.getItem("preferred-music-platform") || "spotify";

  function applyEmbedPreference(platform) {
    const iframes = document.querySelectorAll(".dynamic-music-embed");
    
    iframes.forEach(iframe => {
      let targetSrc = (platform === "apple") 
        ? iframe.getAttribute("data-apple") 
        : iframe.getAttribute("data-spotify");

      if (!targetSrc) {
        targetSrc = iframe.getAttribute("data-spotify") || iframe.getAttribute("data-apple");
      }

      if (targetSrc) {
        targetSrc = targetSrc.replace(/"/g, "");
        iframe.setAttribute("src", targetSrc);
      }
    });
  }

  // Execute immediately to match the user's saved choice
  applyEmbedPreference(savedPlatform);
});
</script>
<script>
  const video = document.getElementById('vid');
  const source = document.getElementById('source');
  
  // Check if screen width is mobile size (768px or less)
  if (window.innerWidth <= 768) {
    source.src = '/imgs/LoaderTQ-1.webm';
    video.load(); // Reload video with the new source
  }
    </script>
</div>

