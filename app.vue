<template>
  <div>
    <!-- Navigation -->
    <nav>
      <NuxtLink to="/">Portfolio</NuxtLink> |
      <NuxtLink to="/about">Wie ben ik</NuxtLink> |
      <NuxtLink to="/contact">Contact</NuxtLink>
    </nav>
    
    <!-- Page Content -->
    <NuxtPage />
  </div>
</template>

<style>
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
  margin-left: 10px;
}
/* Add some basic styling for the navigation links */
nav {
  margin-bottom: 20px;
}

nav a {
  margin-right: 10px;
  text-decoration: none;
  color: #333;
}

nav a:hover {
  text-decoration: underline;
}
.container {
  width: calc(100% - 1000px); /* Subtracting 600px for the 300px gap on both sides */
  margin: 0 auto; /* Horizontally center the container */
  background-color: #8cffa0;
}
@media (max-width: 768px) {
  .container {
    gap: 0;
    padding: 10px 300px;
  }
}
</style>
