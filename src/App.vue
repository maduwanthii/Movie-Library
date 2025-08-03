<template>
  <div id="app">
    <Menu />
    <MovieLibrary />
     <Favority />
     <Reach />
      <Footer />
   </div>
</template>

<script>

import Menu from './components/Header.vue'
import MovieLibrary from './components/MovieLibrary.vue'
import Favority from './components/Favourites.vue'
import Reach from './components/Reach.vue';
import Footer from './components/Footer.vue';

export default {
  name: 'App',
  components: {
    Menu,
    MovieLibrary,
    Favority,
    Reach,
    Footer
   }
}
</script>
