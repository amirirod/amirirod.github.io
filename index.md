---
layout: window
window_title: "About Me"
window_text: "This text loads directly inside the window overlay."
---
 <div style="font-size: 1.5rem; width: 100%; text-align: center; font-family: Palatino;"><span id="date-display" style=" padding: 10px 0px"></span>:</div>

<div>
<div class="content-section" style="background: black; z-index:1">
  <div style="position: sticky; top: 90px; background: black; z-index: 1">
    <p style="text-align: center; font-family: Palatino;">
      <hr>
      <div style="text-align: center; font-family: Palatino;">
       <span id="date-display" style="padding: 10px 0px"></span> 
      </div>
      {% assign today = site.time | date: "%Y-%m-%d" %}

{% for post in site.posts %}
  {% if post.tags contains 'song' %}
    {% assign post_date = post.date | date: "%Y-%m-%d" %}
    {% if post_date == today %}
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
        const today = new Date();
const options = { year: 'numeric', month: 'long', day: 'numeric' };
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
<!--
<ul>
  {% for post in site.posts %}
    {% if post.tags contains 'song' %}
      <li>
        <h2>
          <a class="shrink-btn" onclick="this.parentElement.parentElement.classList.toggle('active');" style="color: #BB0000; letter-spacing: -1px; font-weight: 300; text-decoration: underline white;" href="{{ post.url }}">
            {{ post.date | date: "%B %d, %Y"}} - {{ post.title }}
          </a>
        </h2>
        <div class="post-content" style="font-family: Palatino;">
         {{ post.blurb_text | truncatewords: 40 }}<br>
         TLDR: <u>{{ post.tldr }}</u><br>
         <div>
<iframe 
  data-testid="embed-iframe" 
  style="display: block; border-radius:12px; margin: 0 auto" 
  src= {{ post.spotify_link }} 
  width="100%"
  height="250" 
  frameBorder="0" 
  allowfullscreen="" 
  allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" 
  loading="lazy">
  
</iframe>
</div>
        </div>
        <hr>
      </li>
    {% endif %}
  {% endfor %}
</ul>
-->
<script>
document.addEventListener("DOMContentLoaded", function () {
  const toggleBtn = document.getElementById("music-platform-toggle");
  const iframe = document.getElementById("music-embed");

  // 1. Define your specific embed URLs
const spotifyUrl = "{{ page.spotify_embed }}";
const appleUrl = "{{ page.apple_embed }}";

  // 2. Load the user's saved preference, or default to Spotify
  let savedPlatform = localStorage.getItem("preferred-music-platform") || "spotify";

  // Function to update the UI based on the active platform
  function updateMusicEmbed(platform) {
    if (platform === "apple") {
      iframe.src = appleUrl;
      toggleBtn.textContent = "🎵 Switch to Spotify";
    } else {
      iframe.src = spotifyUrl;
      toggleBtn.textContent = "🎵 Switch to Apple Music";
    }
  }

  // Initial load
  updateMusicEmbed(savedPlatform);

  // 3. Listen for clicks to swap the URLs
  toggleBtn.addEventListener("click", function () {
    if (savedPlatform === "spotify") {
      savedPlatform = "apple";
    } else {
      savedPlatform = "spotify";
    }

    // Save choice to localStorage and update iframe
    localStorage.setItem("preferred-music-platform", savedPlatform);
    updateMusicEmbed(savedPlatform);
  });
});
 </script>
<button id="global-music-toggle" style="margin-bottom: 20px; padding: 10px; border-radius: 8px; cursor: pointer;">
  Switch to Apple Music
</button>

<ul>
  {% for post in site.posts %}
    {% if post.tags contains 'song' %}
      <li>
        <h2>
          <a class="shrink-btn" onclick="this.parentElement.parentElement.classList.toggle('active');" style="color: #BB0000; letter-spacing: -1px; font-weight: 300; text-decoration: underline white;" href="{{ post.url }}">
            {{ post.date | date: "%B %d, %Y"}} - {{ post.title }}
          </a>
        </h2>
        <div class="post-content" style="font-family: Palatino;">
          {{ post.blurb_text | truncatewords: 40 }}<br>
          TLDR: <u>{{ post.tldr }}</u><br>
          <div>
            <!-- 2. CHANGED: Use a class, use data attributes to store both links, and remove the raw src -->
            <iframe 
              class="dynamic-music-embed" 
              data-testid="embed-iframe" 
              style="display: block; border-radius:12px; margin: 0 auto" 
              data-spotify="{{ post.spotify_link }}"
              data-apple="{{ post.apple_link }}" 
              width="100%"
              height="250" 
              frameBorder="0" 
              allowfullscreen="" 
              allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" 
              loading="lazy">
            </iframe>
          </div>
        </div>
        <hr>
      </li>
    {% endif %}
  {% endfor %}
</ul>
</div>
