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
        <li>
          <a href="#" @click.prevent="toggleMenu">
            <img src="/assets/Icons/Menu White.svg" alt="Icon" />
          </a>
        </li>
      </ul>
    </nav>

    <div :class="['menu-panel', { show: isMenuOpen }]" v-if="isMenuOpen">
      <button class="close-button" @click="toggleMenu">×</button>
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
  name: "Menu",
  data() {
    return {
      isMenuOpen: false,
    };
  },
  methods: {
    toggleMenu() {
      this.isMenuOpen = !this.isMenuOpen;
    },
  },
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
  margin: 0;
}

nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
  max-width: 1280px;
  margin: 0 auto;
}

.logo img {
  height: 30px;
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
  font-family: "Lucida Sans Unicode", "Lucida Grande", Geneva, Verdana,
    sans-serif;
  color: white;
  text-decoration: none;
  font-weight: 300;
  font-size: 11px;
  letter-spacing: 0.05em;
  text-transform: uppercase;
}

.head-menu li:nth-child(-n + 5) a {
  font-family: "Lucida Sans Unicode", "Lucida Grande", Geneva, Verdana,
    sans-serif;
  font-size: 11px;
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

.menu-panel {
  position: fixed;
  top: 0;
  right: 0;
  left: auto;
  height: 100vh;
  background-color: rgba(0, 0, 0, 0.95);
  z-index: 200;
  padding: 2rem;
  display: flex;
  flex-direction: column;
  align-items: flex-start; /* Left align contents */
  justify-content: flex-start;
  text-align: left;

  width: 100%;
  transform: translateX(100%);
  transition: transform 0.3s ease-in-out;
}

.menu-panel.show {
  transform: translateX(0);
}

.panel-links {
  list-style: none;
  padding: 0;
  margin-top: 2rem;
  width: 100%;

  display: flex;
  flex-direction: column;
  align-items: flex-start; /* Left align list items */
}

.panel-links li {
  margin-bottom: 1rem;
}

.panel-links a {
  color: white;
  font-family: "Lucida Sans Unicode", "Lucida Grande", Geneva, Verdana,
    sans-serif;
  font-size: 11px;
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

@media (max-width: 768px) {
  .head-menu li:not(:last-child) {
    display: none;
  }

  .head-menu {
    gap: 0;
  }

  nav {
    padding: 0 1rem;
  }

  .menu-panel {
    width: 100%;
  }
}

@media (max-width: 1024px) and (min-width: 769px) {
  .menu-panel {
    width: 33.3333%;
  }

  .head-menu li {
    display: list-item;
  }

  .close-button {
    top: 1rem;
    right: 1.5rem;
  }
}
</style>
