---
tags: menu
title: search
layout: window
---
<head>
  <meta charset="UTF-8" />
  <style>
    .mark-toggle {
      padding: 6px 12px;
      margin: 4px;
      background: #black !important;
      color: #222;
      cursor: pointer;
    }
    #mark-buttons .mark-toggle.active {
      color: #ffffff !important;
      border-color: #DD756E !important;
    }
    .tag-group {
      margin-top: 1.25rem;
    }
    .tag-group ul {
      list-style: disc;
      padding-left: 1.5rem;
    }
    .post-item {
      margin: 0.25rem 0;
    }
    .doors {
      background: #808C93 !important;
      text-color: #000001 !important;
      }
  </style>
</head>
  <header class="post-header">
    <h1 class="post-title"></h1>
  </header>

  <!-- 1. Gather unique marks using Liquid -->
  {% assign all_marks = "" | split: "" %}
  {% for post in site.posts %}
    {% if post.mark %}
      {% assign mark_list = post.mark | join: "," | split: "," %}
      {% for m in mark_list %}
        {% assign trimmed = m | strip %}
        {% if trimmed != "" %}
          {% assign all_marks = all_marks | push: trimmed %}
        {% endif %}
      {% endfor %}
    {% endif %}
  {% endfor %}
  {% assign unique_marks = all_marks | uniq | sort %}
<div>
<div class="content-section" style="background: black; z-index:1">
  <div style="position: sticky; top: 90px; background: black; z-index: 5">
    <p style="text-align: center; font-family: Palatino;">
    <div style="text-align: center; font-family: Palatino;">
         <!-- 2. Render the selectable toggle buttons -->
  <div id="mark-buttons">
    {% for mark in unique_marks %}
      <button type="button" class="mark-toggle" data-mark="{{ mark | slugify }}">
        {{ mark }}
      </button>
    {% endfor %}
  </div>
      </div>
      <hr>
        <!-- 3. Display the list of currently selected marks -->
  <div>
    <strong>Selected Marks:</strong>
    <ul id="selected-marks-list">
      <li class="empty-msg">None selected</li>
    </ul>
  </div>
    </p>
    <div style="
    background-image: url('/imgs/Untitled15.png');
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
</div>
  <!-- 4. Render posts grouped by tag, hiding tag sections with no matching posts -->
  <div id="posts-list">
    {% for tag in site.tags %}
      {% assign tag_name = tag[0] %}
      {% assign tag_posts = tag[1] %}
      {% assign marked_posts = "" | split: "" %}
      {% for post in tag_posts %}
        {% if post.mark %}
          {% assign raw_marks = post.mark | join: "," | split: "," %}
          {% assign has_valid_mark = false %}
          {% for m in raw_marks %}
            {% if m | strip != "" %}
              {% assign has_valid_mark = true %}
            {% endif %}
          {% endfor %}
          {% if has_valid_mark %}
            {% assign marked_posts = marked_posts | push: post %}
          {% endif %}
        {% endif %}
      {% endfor %}
      {% if marked_posts.size > 0 %}
        <section class="tag-group" data-tag="{{ tag_name | slugify }}">
          <h2>{{ tag_name }}</h2>
          <ul>
            {% for post in marked_posts %}
              {% assign post_marks = "" | split: "" %}
              {% assign raw_marks = post.mark | join: "," | split: "," %}
              {% for m in raw_marks %}
                {% assign trimmed = m | strip %}
                {% if trimmed != "" %}
                  {% assign slug = trimmed | slugify %}
                  {% assign post_marks = post_marks | push: slug %}
                {% endif %}
              {% endfor %}
              {% assign unique_post_marks = post_marks | uniq %}
              <li class="post-entry" data-marks="{{ unique_post_marks | join: ',' }}">
                <article class="post-item">
                  <a style="color: #DD756E;" href="{{ post.url | relative_url }}">{{ post.title }}</a>
                </article>
              </li>
            {% endfor %}
          </ul>
        </section>
      {% endif %}
    {% endfor %}
  </div>

  <p id="no-matches-msg" style="display: none;">No posts match the selected marks.</p>

  <script>
    document.addEventListener("DOMContentLoaded", () => {
      const buttons = document.querySelectorAll(".mark-toggle");
      const selectedList = document.getElementById("selected-marks-list");
      const tagGroups = document.querySelectorAll(".tag-group");
      const noMatchesMsg = document.getElementById("no-matches-msg");

      // Store active marks: slug -> label
      const selectedMarks = new Map();

      buttons.forEach((button) => {
        button.addEventListener("click", () => {
          const slug = button.dataset.mark;
          const label = button.textContent.trim();

          if (selectedMarks.has(slug)) {
            selectedMarks.delete(slug);
            button.classList.remove("doors");
          } else {
            selectedMarks.set(slug, label);
            button.classList.add("doors");
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

        selectedMarks.forEach((label) => {
          const li = document.createElement("li");
          li.textContent = label;
          selectedList.appendChild(li);
        });
      }

      function filterPosts() {
        const activeSlugs = Array.from(selectedMarks.keys());
        let totalVisiblePosts = 0;

        tagGroups.forEach((group) => {
          const entries = group.querySelectorAll(".post-entry");
          let visibleInGroup = 0;

          entries.forEach((entry) => {
            const postMarks = entry.dataset.marks ? entry.dataset.marks.split(",") : [];

            // Show all when none selected; otherwise require every selected mark
            // (change `.every` to `.some` if you want any selected mark to match)
            const isMatch =
              activeSlugs.length === 0 ||
              activeSlugs.every((slug) => postMarks.includes(slug));

            entry.style.display = isMatch ? "" : "none";
            if (isMatch) {
              visibleInGroup += 1;
            }
          });

          // Only display the tag section if at least one post in it is visible
          group.style.display = visibleInGroup > 0 ? "" : "none";
          totalVisiblePosts += visibleInGroup;
        });

        if (noMatchesMsg) {
          noMatchesMsg.style.display = totalVisiblePosts === 0 ? "" : "none";
        }
      }
    });
  </script>
