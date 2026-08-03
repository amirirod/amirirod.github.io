---
layout: page
title: Blog Archive
tags: menu
---
<html>
<style>
.dropdown {
  position: relative;
  display: inline-block;
}

.dropdown-content {
  display: none;
  position: absolute;
  background-color: #f1f1f1;
  min-width: 160px;
  box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.2);
  z-index: 1;
}

/* Links inside the dropdown */
.dropdown-content a {
  color: black;
  padding: 12px 16px;
  text-decoration: none;
  display: block;
}

/* Change color of dropdown links on hover */
.dropdown-content a:hover {
  background-color: #ddd;
}

/* SHOW the dropdown menu when hovering over the container */
.dropdown:hover .dropdown-content {
  display: block;
  }
</style>

{% for tag in site.tags %}
  <!-- Use the tag name to create a unique ID for JavaScript to target -->
  <h3>
    <button style="width: 100%; font-size: 1.2rem; font-weight: 300; font-family: Palatino" onclick="toggleTagList('{{ tag[0] | slugify }}')">
      {{ tag[0] }}
    </button>
  </h3>
  
  
  <!-- The list starts hidden by default using display:none -->
  <ul id="{{ tag[0] | slugify }}" style="display: none;">
    {% for post in tag[1] %}
      <li>
        <a href="{{ post.url }}">{{ post.date | date: "%B %d, %Y"}} - {{ post.title }}</a>
      </li>
    {% endfor %}
  </ul>
  <hr>
{% endfor %}
</div>
<script>
function toggleTagList(tagId) {
  var x = document.getElementById(tagId);
  if (x.style.display === "none" || x.style.display === "") {
    x.style.display = "block";
  } else {
    x.style.display = "none";
  }
}
</script>
</html>

