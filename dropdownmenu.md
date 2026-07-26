---

title: Select
---

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
<div class="dropdown">
  <button class="dropbtn">Hover Me</button>
  <div class="dropdown-content">
    <a class="post_navi-item nav_next" href="{{ 'albums.html' | absolute_url }}" title="Albums">Albums</a>
    <a href="#">Link 2</a>
    <a href="#">Link 3</a>
  </div>
</div>


