<template>
  <div id="app">
   <Header 
   @sendSelect="getSelect($event)"
   />
   <Main 
   :inputHeader="valueHeader"
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
      valueHeader: ""
    }
  },
  methods: {
    getSelect(value) {
      this.valueHeader = value
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
