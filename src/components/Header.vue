<template>
  <header>
    <nav>
      <div class="logo">
        <img src="/assets/Logos/Logo White.svg" alt="Cinema Logo" />
      </div>
      <ul class="head-menu">
        <li><a href="#">HOME</a></li>
        <li><a href="#">OUR SCREENS</a></li>
        <li><a href="#">SCHEDULE</a></li>
        <li><a href="#">MOVIE LIBRARY</a></li>
        <li><a href="#">LOCATION & CONTACT</a></li>
        <li><a href="#"><img src="/assets/Icons/Menu White.svg" alt="Icon" /></a></li>
      </ul>
    </nav>
    <div v-if="isMenuOpen" class="menu-panel">
  <button class="close-button" @click="toggleMenu">✕</button>
  <ul class="panel-links">
    <li><a href="#">LOCATION & CONTACT</a></li>
    <li><a href="#">GALLERY</a></li>
  </ul>
</div>
  </header>
     <hr class="favority-hr" />
</template>


<script>
export default {
  name: 'Menu',
  data() {
    return {
      isMenuOpen: false
    };
  },
  methods: {
    toggleMenu() {
      this.isMenuOpen = !this.isMenuOpen;
    }
  }
};
</script>

<style scoped>
header {
  background-color: #000;
  color: white;
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  padding: 1rem 2rem;
  width: 100%;
  z-index: 100;
}

.favority-hr {
  border: none;
  border-top: 0.5px solid #555;
  margin: 0px
}
.Cinema Logo img {
  height: 20px;
}


nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
  max-width: 1280px;
  margin: 0 auto;
}

.head-menu {
  display: flex;
  align-items: center;
  list-style: none;
  gap: 2rem;
  margin: 0;
  padding: 0;
}


.head-menu a {
  color: white;
  text-decoration: none;
  font-weight: 300;
  font-size: 0.9rem;
  letter-spacing: 0.05em;
  text-transform: uppercase;
}


.head-menu a:hover,
.head-menu a:focus {
  text-decoration: underline;
}


.head-menu img {
  height: 20px;
  width: auto;
  padding-left: 0.5rem;
}

.head-menu Icon {
  height: 30px;
  width: auto;
  padding-left: 0.5rem;
}

.menu-panel {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 66vh; /* 2/3 screen height */
  background-color: rgba(0, 0, 0, 0.95);
  z-index: 200;
  padding: 2rem;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  justify-content: flex-start;
}

.panel-links {
  list-style: none;
  padding: 0;
  margin-top: 2rem;
  width: 100%;
}

.panel-links li {
  margin-bottom: 1rem;
}

.panel-links a {
  color: white;
  font-size: 1.1rem;
  text-decoration: none;
  text-transform: uppercase;
  font-weight: 400;
}

.panel-links a:hover {
  text-decoration: underline;
}

.close-button {
  position: absolute;
  top: 1rem;
  right: 1.5rem;
  font-size: 2rem;
  background: none;
  border: none;
  color: white;
  cursor: pointer;
}


</style>
