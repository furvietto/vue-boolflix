<template>
  <div id="app">
   <Header 
   @sendFilms="getFilms($event)"
   @sendMovies="getMovies($event)"
   @sendBooleanFilm="getBooleanFilm($event)"
   @sendBooleanMovies="getBooleanMovies($event)"
   />
   <Main 
   :filmAndMovies="valueAll"
   :valueBooleanFilm="valueBoolFilm"
   :valueBooleanMovies="valueBoolMovies"
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
      valueBoolFilm:null,
      valueBoolMovies:null,
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
    },
    getBooleanFilm(value) {
      this.valueBoolFilm = value
    },
    getBooleanMovies(value) {
      this.valueBoolMovies= value
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
  #app {
    width: 100%;
    height: 100vh;
    overflow: auto;
    background-color: black ;
  }
</style>
