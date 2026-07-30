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
        <h2 ><a class="shrink-btn" onclick="this.parentElement.classList.toggle('active');" style="color: #BB0000; letter-spacing: -1px; font-weight: 300; text-decoration: underline white;" href="{{ post.url }}" >{{ post.date | date: "%B %d, %Y"}} - {{ post.title }}</a>
        </h2>
        <div class="post-content" style="font-family: Palatino;">
  {% assign parts = post.content | split: "Give it a listen:" %}
  {% assign part = parts | markdownify | remove: '</p>' | remove: '<p>' %}
  
  {{ part[0] | strip_html | truncatewords: 40 }} 
  <a href="{{ post.url }}">Read More</a>
  

  {{ part[1] | markdownify | remove: '</p>' }}
        <hr class="custom-divider;" data-darkreader-inline-border-color="grey;" data-darkreader-inline-background-color="#c7b99e">
      </li>
    {% endif %}
  {% endfor %}
</ul>


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

          {% assign parts = post.content | split: "<p>Give it a listen:</p>" %}
 
          {% assign first_part = parts[0] | strip_html | strip %}
          {{ first_part | truncatewords: 40, "" }} 
          <span style="color: grey !important ;"> . . . Read More </span>
 
          {% assign second_part = parts[1] | remove: '<html>' | remove: '</html>' | remove: '<p>' | remove: '</p>' | strip %}
          {{ second_part }}
        </div>
        <hr>
      </li>
    {% endif %}
  {% endfor %}
</ul>
-->
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
         TLDR: <u>{{ post.tldr }}</u><br>
         {{ post.blurb_text | truncatewords: 40 }}<br>
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
</div>
