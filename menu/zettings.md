---
layout: page
title: Settings
tags: menu
---
<h2>Site Preferences</h2>
<p>Choose your preferred default music streaming platform:</p>

<button id="global-music-toggle" style="padding: 10px 20px; border-radius: 8px; cursor: pointer; font-size: 16px;">
  Switch to Apple Music
</button>

<script>
document.addEventListener("DOMContentLoaded", function () {
  const toggleBtn = document.getElementById("global-music-toggle");
  let savedPlatform = localStorage.getItem("preferred-music-platform") || "spotify";

  // Function just to update the button text on the settings page
  function updateButtonLabel(platform) {
    toggleBtn.textContent = (platform === "apple") ? "Switch to Spotify" : "Switch to Apple Music";
  }

  // Set the initial label on load
  updateButtonLabel(savedPlatform);

  // Change the value in LocalStorage when clicked
  toggleBtn.addEventListener("click", function () {
    savedPlatform = (savedPlatform === "spotify") ? "apple" : "spotify";
    localStorage.setItem("preferred-music-platform", savedPlatform);
    updateButtonLabel(savedPlatform);
  });
});
</script>
