<template>
  <div id="app">
    <!-- mettere tutti i gli elementi padri -->
    <Header />
    <Main />
  </div>
</template>

<script>
import Main from "./components/Main.vue";
import Header from "./components/Header.vue";

export default {
  name: "App",
  components: {
    //mettere tutti i gli elementi padri
    Main,
    Header
  },
};
</script>

<style lang="scss">
//mettere elemento scss
@import "./assets/scss/style.scss";
//Botstrap
@import "~bootstrap/scss/bootstrap";
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
