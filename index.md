---
layout: window
window_title: "About Me"
window_text: "This text loads directly inside the window overlay."
---
Just some music.
<button onclick="openWindow();" style="background:none; border:none; padding:0; cursor:pointer; z-index: 6000">
  Test
</button>
<div>
<div class="content-section">
  <div style="position: sticky; top: 90px; background: black; z-index: 0">
    <p style="text-align: center; font-family: Palatino;">
      <span id="date-display"></span>:
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
Most Recent Song of The Day:
<ul>
  {% for post in site.posts %}
    {% if post.tags contains 'song' %}
      <li>
        <h2 ><a style="color: #BB0000; letter-spacing: -1px; font-weight: 300; text-decoration: underline white;" href="{{ post.url }}">{{ post.date | date: "%B %d, %Y"}} - {{ post.title }}</a>
        </h2>
        <div class="post-content;" style="font-family: Palatino">
          {{ post.content }}
        </div>
        <hr class="custom-divider;" data-darkreader-inline-border-color="grey;" data-darkreader-inline-background-color="#c7b99e">
      </li>
    {% endif %}
  {% endfor %}
</ul>
</div>
