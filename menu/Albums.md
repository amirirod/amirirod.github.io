---
layout: window
window_title: "About Me"
window_text: "This text loads directly inside the window overlay."
tags: menu
title: Albums of the Month
---

<!--
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
      {% assign this-month = site.time | date: "%Y-%m" %}

{% for post in site.posts %}
  {% if post.tags contains 'album' %}
    {% assign post_date = post.date | date: "%Y-%m" %}
    {% if post_date == this-month %}
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
    border-block: 1px solid grey;">
    </div>
    

 
  </div>
  

 <script>
        const today = new Date();
const options = { month: 'long' ,  year: 'numeric', };
const formattedDate = today.toLocaleDateString(undefined, options); 
document.getElementById('date-display').textContent = formattedDate;
    </script>
   <script>
  const limit = 10; // Change this to your preferred word count
  const element = document.getElementById("truncated-text");
  const words = element.innerText.split(" "); // Split text into words by spaces

  if (words.length > limit) {
    element.innerText = words.slice(0, limit).join(" ") + "...";
  }
</script>



<ul>
  {% for post in site.posts %}
    {% if post.tags contains 'album' %}
      <li>
        <h2>
          <a class="shrink-btn" onclick="this.parentElement.parentElement.classList.toggle('active');" style="color: #BB0000; letter-spacing: -1px; font-weight: 300; text-decoration: underline white;" href="{{ post.url }}">
            {{ post.date | date: "%B %Y"}} - {{ post.title }}
          </a>
        </h2>
       <div class="post-content" style="font-family: Palatino;">
  <!-- Enclosing the text string prevents it from merging into the iframe markup -->
  <p style="margin-bottom: 10px;">
    {{ post.blurb_text | truncatewords: 40 }}
  </p>
  TLDR: <u>{{ post.tldr }}</u><br><br> 
  <!-- BACKGROUND WRAPPER CONTAINER (250px tall) -->
  <div style="position: relative; width: 100%; height: 120px; background-image: url('/imgs/Back.png'); box-sizing: border-box; overflow: hidden; padding: 10px">
    <!-- Loader video stays perfectly centered behind the frame -->
    <video autoplay muted loop playsinline 
           style="position: absolute; top: 50%; left: 50%; transform: translate(-50%, -50%); width: 100px; height: 100px; object-fit: contain; z-index: 1; pointer-events: none;">
        <source src="/imgs/LoaderTQ-1.mov" type="video/QuickTime" style="background: transparent !important">
    </video>
    <!-- THE FIX: A layout boundary container that sits exactly 10px away from the edge -->
    <div style="position: absolute; width: 365px; border-radius: 12px; overflow: hidden; z-index: 3;">
      <iframe 
        class="dynamic-music-embed" 
        data-testid="embed-iframe" 
        style="height: 120px; border: none;" 
        data-spotify="{{ post.spotify_link }}"
        data-apple="{{ post.apple_link }}"
        allowfullscreen="" 
        allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" 
        loading="lazy">
      </iframe>
    </div>
  </div>
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
        iframe.setAttribute("height", "100%");
        iframe.setAttribute("width", "100%");
      }
    });
  }
  applyEmbedPreference(savedPlatform);
});
</script>
</div>
