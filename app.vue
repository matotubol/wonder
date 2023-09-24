<template>
  <div>
    <!-- Navigation -->
    <div class="nav-header">
      <nav>
      <NuxtLink to="/">Portfolio</NuxtLink>
      <NuxtLink to="/about">Wie ben ik</NuxtLink>
      <NuxtLink to="/contact">Contact</NuxtLink>
    </nav>
    </div>

    <!-- Page Content -->
    <div class="container">
      <NuxtPage />

    </div>
  </div>
</template>

<style>
.nav-header {
  position: relative;
  height: 120px;
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 10px;
  border-top: 3px solid #f4e0c0;
  border-bottom: 3px solid #f4e0c0;
  margin-bottom: 50px;
}

.nav-header::before,
.nav-header::after {
  content: "";
  position: absolute;
  left: 0;
  right: 0;
  height: 2px;
  background-color: #f4e0c0;
}

.nav-header::before {
  top: -8px; /* Adjusted to create a 5px gap between the lines */
}

.nav-header::after {
  bottom: -8px; /* Adjusted to create a 5px gap between the lines */
}

@font-face {
        font-family: "Caudex";
        src: url("/fonts/Caudex-Regular.ttf") format("woff2");
}

*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  background-color: #F9E7C7;
  font-family: Caudex, sans-serif;
}

p {
  margin-bottom: 20px;
}
/* Add some basic styling for the navigation links */
nav {
  margin-bottom: 20px;
}

nav a {
  margin-right: 20px;
  text-decoration: none;
  color: #333;
}

nav a:hover {
  text-decoration: none;
  font-weight: bold;
  color: #FF4040;
}
.container {
  display: flex;
  justify-content: center;
  min-height: 100vh; /* Updated from height to min-height */}

  img:hover{
    opacity: .8;
    cursor: pointer;
  }
</style>
