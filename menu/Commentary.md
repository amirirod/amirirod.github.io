---
layout: window
title: Commentary
tags: menu
window_title: "About Me"
---
 <div style="font-size: 1.5rem; width: 100%; text-align: center; font-family: Palatino;"><span id="date-display" style=" padding: 10px 0px"></span>:</div>

<div>
<div class="content-section" style="background: black; z-index:1">
  <div style="position: sticky; top: 90px; background: black; z-index: 5">
    <p style="text-align: center; font-family: Palatino;">
      <hr>
      <div style="text-align: center; font-family: Palatino;">
       <span id="date-display" style="padding: 10px 0px"></span> 
      </div>
      {% assign today = site.time | date: "%Y-%m-%d" %}
{% assign found_today_post = false %}

{% for post in site.posts %}
  {% if post.tags contains 'commentary' %}
    {% assign post_date = post.date | date: "%Y-%m-%d" %}
    {% if post_date == today %}
      {% assign found_today_post = true %}
      <div class="post-content" style="text-align:center; font-size: 2.5rem; font-family: Palatino; margin-bottom: 0px">
        {{ post.title }}
      </div>
    {% endif %}
    
  {% endif %}
{% endfor %}

{% if found_today_post == false %}
  <div class="post-content" style="text-align:center; font-size: 2.5rem; font-family: Palatino; margin-bottom: 0px">
    Nothing to say today
  </div>
{% endif %}
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



<ul>
  {% for post in site.posts %}
    {% if post.tags contains 'commentary' %}
      <li>
        <h2>
          <a class="shrink-btn" onclick="this.parentElement.parentElement.classList.toggle('active');" style="color: #BB0000; letter-spacing: -1px; font-weight: 300; text-decoration: underline white;" href="{{ post.url }}">
            {{ post.date | date: "%B %d, %Y"}} - {{ post.title }}
          </a>
        </h2>
        <div class="post-content" style="font-family: Palatino;">
          <!-- Enclosing the text string prevents it from merging into the iframe markup -->
          <p style="margin-bottom: 10px;">
            {{ post.blurb_text | truncatewords: 40 }}
          </p>
          TLDR: <u>{{ post.tldr }}</u><br><br>
        </div>
        <hr>
      </li>
    {% endif %}
  {% endfor %}
</ul>

</div>
