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
    gap: 16px;
    max-width: 600px;
    margin: 40px auto;
    font-family: sans-serif;
  }

  /* 3 columns x 3 rows grid */
  .grid-container {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-template-rows: repeat(3, 100px); /* 3 rows high */
    gap: 12px;
    flex: 1;
  }

  .grid-item {
    background-color: #f0f4f8;
    border: 1px solid #cbd5e1;
    border-radius: 8px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-weight: bold;
    color: #334155;
  }

  .arrow-btn {
    background: #2563eb;
    color: white;
    border: none;
    border-radius: 50%;
    width: 40px;
    height: 40px;
    font-size: 18px;
    cursor: pointer;
  }

  .arrow-btn:disabled {
    background: #cbd5e1;
    cursor: not-allowed;
  }
</style>
</head>
<body>

<div class="carousel-wrapper">
  <button class="arrow-btn" id="prevBtn">&#8592;</button>
  
  <div class="grid-container" id="grid">
    <!-- Items go here -->
    <div class="grid-item">Item 1</div>
    <div class="grid-item">Item 2</div>
    <div class="grid-item">Item 3</div>
    <div class="grid-item">Item 4</div>
    <div class="grid-item">Item 5</div>
    <div class="grid-item">Item 6</div>
    <div class="grid-item">Item 7</div>
    <div class="grid-item">Item 8</div>
    <div class="grid-item">Item 9</div>
    <!-- Page 2 -->
    <div class="grid-item">Item 10</div>
    <div class="grid-item">Item 11</div>
    <div class="grid-item">Item 12</div>
    <div class="grid-item">Item 13</div>
    <div class="grid-item">Item 14</div>
    <div class="grid-item">Item 15</div>
  </div>

  <button class="arrow-btn" id="nextBtn">&#8594;</button>
</div>

<script>
  const items = Array.from(document.querySelectorAll('.grid-item'));
  const prevBtn = document.getElementById('prevBtn');
  const nextBtn = document.getElementById('nextBtn');
  
  const itemsPerPage = 9; // 3 rows x 3 columns
  let currentPage = 0;
  const totalPages = Math.ceil(items.length / itemsPerPage);

  function updateGrid() {
    const start = currentPage * itemsPerPage;
    const end = start + itemsPerPage;

    // Show only the 9 items for the current page
    items.forEach((item, index) => {
      item.style.display = (index >= start && index < end) ? 'flex' : 'none';
    });

    // Disable arrows at the first and last pages
    prevBtn.disabled = currentPage === 0;
    nextBtn.disabled = currentPage >= totalPages - 1;
  }

  prevBtn.addEventListener('click', () => {
    if (currentPage > 0) {
      currentPage--;
      updateGrid();
    }
  });

  nextBtn.addEventListener('click', () => {
    if (currentPage < totalPages - 1) {
      currentPage++;
      updateGrid();
    }
  });

  // Initialize first page
  updateGrid();
</script>

</body>
</html>
