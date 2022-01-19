<template>
  <div id="app">
   <Header 
   @sendSelect="getSelect($event)"
   @sendError="getError($event)"
   />
   <Main 
   :inputHeader="valueHeader"
    :inputError="errorHeader"
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
      valueHeader: null,
      errorHeader: null,
    }
  },
  methods: {
    getSelect(value) {
      this.valueHeader = value
    },
    getError(value) {
      this.errorHeader = value
    },
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
