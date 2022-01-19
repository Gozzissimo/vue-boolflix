<template>
  <div id="app">
    <Header />
    <Main />
  </div>
</template>

<script>
import Main from "./components/Main.vue";
import Header from "./components/Header.vue";
import Header from "./components/FilmCard.vue";


export default {
  name: "App",
  components: {
    Main,
    Header,
    FilmCard,
  },
};
</script>

<style lang="scss">
#app {

}
</style>
