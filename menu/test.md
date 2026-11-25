---
tags: menu
title: test
---

{% assign all_marks = "" | split: "" %}
{% for post in site.posts %}
  {% if post.mark %}
    {% assign all_marks = all_marks | concat: post.mark %}
  {% endif %}
{% endfor %}
{% assign unique_marks = all_marks | uniq | sort %}

<!-- Available Marks -->
<div id="available-marks">
  <h3>Available Marks</h3>
  {% for mark in unique_marks %}
    <button type="button" class="mark-btn" data-mark="{{ mark | slugify }}">
      {{ mark }}
    </button>
  {% endfor %}
</div>

<!-- Selected Marks -->
<div id="selected-marks">
  <h3>Selected Marks</h3>
  <div id="selected-list"></div>
</div>

<!-- Posts List -->
<ul id="post-list">
  {% for post in site.posts %}
    {% capture post_marks %}{% for m in post.mark %}{{ m | slugify }},{% endfor %}{% endcapture %}
    <li class="post-item" data-marks="{{ post_marks }}">
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>



<script>
  document.addEventListener("DOMContentLoaded", () => {
    const selectedMarks = new Set();
    const availableContainer = document.getElementById("available-marks");
    const selectedList = document.getElementById("selected-list");
    const posts = document.querySelectorAll(".post-item");

    // Handle clicking an available mark
    availableContainer.addEventListener("click", (e) => {
      if (!e.target.classList.contains("mark-btn")) return;

      const btn = e.target;
      const mark = btn.dataset.mark;

      if (!selectedMarks.has(mark)) {
        selectedMarks.add(mark);
        btn.disabled = true; // Visually disable in the original list

        // Create a button in the "Selected" list to allow removing it
        const selectedBtn = document.createElement("button");
        selectedBtn.textContent = `${btn.textContent.trim()} ✕`;
        selectedBtn.dataset.mark = mark;
        selectedBtn.addEventListener("click", () => {
          selectedMarks.delete(mark);
          selectedBtn.remove();
          btn.disabled = false;
          filterPosts();
        });

        selectedList.appendChild(selectedBtn);
        filterPosts();
      }
    });

    // Show posts that contain ALL selected marks (AND logic)
    function filterPosts() {
      posts.forEach((post) => {
        const postMarks = post.dataset.marks.split(",").filter(Boolean);
        const matchesAll = Array.from(selectedMarks).every((m) =>
          postMarks.includes(m)
        );

        post.style.display =
          selectedMarks.size === 0 || matchesAll ? "" : "none";
      });
    }
  });
</script>

<style>
  .mark-btn.active {
    background-color: #007bff;
    color: white;
  }
</style>
