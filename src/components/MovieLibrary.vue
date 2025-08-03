<template>
  <div class="movie-library-page">
    <!-- Header -->
   

    <hr />

    <!-- Hero Image -->
    <section class="hero">
      <img src="/assets/Images/Header Image2.jpg" alt="Theater" />
    </section>

   
    <section class="movie-intro">
      <h2>Movie Library</h2>
      <p>
        Lorem ipsum dolor sit amet, consetetur sadipscing elitr,<br />
        sed diam nonumy eirmod tempor invidunt ut labore et <br />
        dolore magna aliquyam erat, sed diam voluptua.
      </p>
    </section>
  </div>
</template>

<script>
export default {
  name: "MovieLibrary",
};
</script>

<!-- Global styles -->
<style>
html, body, #app {
  margin: 0;
  padding: 0;
  height: 100%;
  width: 100%;
  background-color: black; /* Ensure full background black */
  overflow-x: hidden;
  font-family: Arial, sans-serif;
  scrollbar-width: none;
}
*, *::before, *::after {
  box-sizing: border-box;
}
</style>

<!-- Scoped styles -->
<style scoped>
.movie-library-page {
  color: white;
  background-color: black;
  min-height: 100vh;
  width: 100%;
  overflow-x: hidden;
}

/* Header */
.site-header {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  height: 60px;
  background-color: #000;
  z-index: 100;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 1rem 2rem;
}

.logo img {
  height: 30px;
}

.main-nav ul {
  list-style: none;
  display: flex;
  gap: 1.5rem;
  margin: 0;
  padding: 0;
}

.main-nav a {
  text-decoration: none;
  color: white;
  font-weight: bold;
}

.main-nav a:hover {
  text-decoration: underline;
}

/* Hero Image */
.hero {
  margin-top: 60px; /* below fixed header */
  height: calc(100vh - 60px);
  width: 100%;
}

.hero img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

/* Intro Section */
.movie-intro {
  padding: 2rem;
  text-align: left;
}

.movie-intro h2 {
  font-size: 2rem;
  margin-bottom: 1rem;
  text-transform: uppercase;
}

.movie-intro p {
  color: #ccc;
  line-height: 1.6;
}

/* Responsive */
@media (max-width: 768px) {
  .main-nav {
    display: none;
  }
}
</style>
