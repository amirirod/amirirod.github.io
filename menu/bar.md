---
tags: menu
title: bar
---
<html lang="en">
<head>
<meta charset="UTF-8">
<style>
  .carousel-wrapper {
    display: flex;
    align-items: center;
    gap: 12px;
    max-width: 600px;
    margin: 40px auto;
    font-family: sans-serif;
  }

  /* Grid that flows by column, wrapping after 3 rows */
  .grid-pages {
    display: grid;
    grid-auto-flow: column;
    grid-template-rows: repeat(3, 1fr); /* Wraps 3 times (3 rows) */
    grid-auto-columns: 100%;            /* Each column takes 100% width (1 page) */
    overflow-x: auto;
    scroll-snap-type: x mandatory;
    scroll-behavior: smooth;
    gap: 10px;
    width: 100%;
    
    /* Hide scrollbar for a cleaner look */
    scrollbar-width: none; 
  }
  .grid-pages::-webkit-scrollbar {
    display: none;
  }

  .item {
    scroll-snap-align: start;
    background: #f0f4f8;
    border: 1px solid #d1d9e0;
    border-radius: 8px;
    padding: 20px;
    text-align: center;
    font-weight: bold;
  }

  .nav-btn {
    background: #007bff;
    color: white;
    border: none;
    border-radius: 50%;
    width: 40px;
    height: 40px;
    font-size: 18px;
    cursor: pointer;
    flex-shrink: 0;
  }
  .nav-btn:hover {
    background: #0056b3;
  }
</style>
</head>
<body>

<div class="carousel-wrapper">
  <button class="nav-btn" onclick="scrollPage(-1)">&#8592;</button>

  <div class="grid-pages" id="pageContainer">
    <!-- Page 1 -->
    <div class="item">Item 1</div>
    <div class="item">Item 2</div>
    <div class="item">Item 3</div>
    <!-- Page 2 -->
    <div class="item">Item 4</div>
    <div class="item">Item 5</div>
    <div class="item">Item 6</div>
    <!-- Page 3 -->
    <div class="item">Item 7</div>
    <div class="item">Item 8</div>
  </div>

  <button class="nav-btn" onclick="scrollPage(1)">&#8594;</button>
</div>

<script>
  function scrollPage(direction) {
    const container = document.getElementById('pageContainer');
    // Scroll by the exact width of one visible page
    container.scrollBy({
      left: direction * container.clientWidth,
      behavior: 'smooth'
    });
  }
</script>

</body>
</html>
