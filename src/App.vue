<template>
  <div id="app">
   <Header 
   @sendFilms="getFilms($event)"
   @sendMovies="getMovies($event)"
   />
   <Main 
   :filmAndMovies="valueAll"
   
   />
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Main from './components/Main.vue'

export default {
  name: "App",
  data() {
    return {
      valueAll: {
        films:[],
        movie:[]
      }
    }
  },
  methods: {
    getFilms(value) {
      this.valueAll.films = value
    },
    getMovies(value) {
      this.valueAll.movie = value
    }
  },

  components: {
    Header,
    Main,
  },
};
</script>

<style lang="scss">
  @import "~bootstrap/scss/bootstrap";
</style>
