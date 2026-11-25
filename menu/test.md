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
{% assign unique_marks = all_marks | uniq %}

<h3>Available Marks</h3>
<div id="available-marks">
  {% for mark in unique_marks %}
    <button type="button" class="mark-btn" data-mark="{{ mark | escape }}">
      {{ mark }}
    </button>
  {% endfor %}
</div>

<h3>Selected Marks</h3>
<ul id="selected-marks"></ul>

<script>
  document.addEventListener('DOMContentLoaded', () => {
    const buttons = document.querySelectorAll('.mark-btn');
    const selectedList = document.getElementById('selected-marks');
    const selectedMarks = new Set();

    buttons.forEach(button => {
      button.addEventListener('click', () => {
        const mark = button.dataset.mark;

        // Toggle selection state
        if (selectedMarks.has(mark)) {
          selectedMarks.delete(mark);
          button.classList.remove('active');
        } else {
          selectedMarks.add(mark);
          button.classList.add('active');
        }

        // Re-render the selected list
        selectedList.innerHTML = '';
        selectedMarks.forEach(item => {
          const li = document.createElement('li');
          li.textContent = item;
          selectedList.appendChild(li);
        });
      });
    });
  });
</script>

<style>
  .mark-btn.active {
    background-color: #007bff;
    color: white;
  }
</style>
