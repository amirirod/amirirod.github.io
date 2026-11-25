---
tags: menu
title: test
---

<!-- 1. Gather unique marks using Liquid -->
{% assign all_marks = "" | split: "" %}
{% for post in site.posts %}
  {% if post.mark %}
    {% assign all_marks = all_marks | concat: post.mark %}
  {% endif %}
{% endfor %}
{% assign unique_marks = all_marks | uniq | sort %}

<!-- 2. Render the selectable toggle buttons -->
<div id="mark-buttons">
  {% for mark in unique_marks %}
    <button type="button" class="mark-toggle" data-mark="{{ mark | slugify }}">
      {{ mark }}
    </button>
  {% endfor %}
</div>

<!-- 3. Display the list of currently selected marks -->
<div>
  <strong>Selected Marks:</strong>
  <ul id="selected-marks-list">
    <li class="empty-msg">None selected</li>
  </ul>
</div>

<!-- 4. Render all posts with their marks attached as data attributes -->
<div id="posts-list">
  {% for post in site.posts %}
    {% assign post_marks = "" | split: "" %}
    {% for mark in post.mark %}
      {% assign slug = mark | slugify %}
      {% assign post_marks = post_marks | push: slug %}
    {% endfor %}
    
    <article class="post-item" data-marks="{{ post_marks | join: ',' }}">
      <h3><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
    </article>
  {% endfor %}
</div>


<script>
document.addEventListener("DOMContentLoaded", () => {
  const buttons = document.querySelectorAll(".mark-toggle");
  const selectedList = document.getElementById("selected-marks-list");
  const posts = document.querySelectorAll(".post-item");
  
  // Store active marks (using a Map to keep both slug and display label)
  const selectedMarks = new Map();

  buttons.forEach(button => {
    button.addEventListener("click", () => {
      const slug = button.dataset.mark;
      const label = button.textContent.trim();

      // Toggle selection state
      if (selectedMarks.has(slug)) {
        selectedMarks.delete(slug);
        button.classList.remove("active");
      } else {
        selectedMarks.set(slug, label);
        button.classList.add("active");
      }

      updateSelectedList();
      filterPosts();
    });
  });

  function updateSelectedList() {
    selectedList.innerHTML = "";
    
    if (selectedMarks.size === 0) {
      selectedList.innerHTML = '<li class="empty-msg">None selected</li>';
      return;
    }

    selectedMarks.forEach((label, slug) => {
      const li = document.createElement("li");
      li.textContent = label;
      selectedList.appendChild(li);
    });
  }

  function filterPosts() {
    const activeSlugs = Array.from(selectedMarks.keys());

    posts.forEach(post => {
      // If no marks are selected, show all posts
      if (activeSlugs.length === 0) {
        post.style.display = "";
        return;
      }

      const postMarks = post.dataset.marks ? post.dataset.marks.split(",") : [];
      
      // Check if the post includes EVERY selected mark (use .some instead of .every for OR logic)
      const matchesAll = activeSlugs.every(slug => postMarks.includes(slug));
      
      post.style.display = matchesAll ? "" : "none";
    });
  }
});
</script>
<style>
.mark-toggle {
  padding: 6px 12px;
  margin: 4px;
  border: 1px solid #ccc;
  background: #f9f9f9;
  cursor: pointer;
  border-radius: 4px;
}

.mark-toggle.active {
  background: #007bff;
  color: white;
  border-color: #0056b3;
}
</style>
