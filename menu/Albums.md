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
        
        // --- THE FIX: FORCING FIXED PIXEL DIMENSIONS ---
        // Spotify and Apple Music engines require real integer heights to render full cards.
        // 250px container height minus 20px padding leaves exactly 230px of vertical space.
        iframe.setAttribute("height", "230"); 
        iframe.style.setProperty('height', '230px', 'important');
      }
    });
  }

  // Execute immediately to match the user's saved choice
  applyEmbedPreference(savedPlatform);
});
</script>
        </div>
        <hr>
      </li>
    {% endif %}
  {% endfor %}
</ul>
<script>
document.addEventListener("DOMContentLoaded", function () {
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
        // --- THE FIXED JAVASCRIPT FORCE OVERRIDE ---
        // Forces Spotify/Apple's engines to drop the compact 80px/152px layout
        iframe.setAttribute("height", "230"); 
        iframe.style.setProperty('height', '230px', 'important');
      }
    });
  }

  applyEmbedPreference(savedPlatform);
});
</script>
</div>
