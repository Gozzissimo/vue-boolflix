<template>
  <div id="app">
    <Header 
      @mergedList="setMovieList($event)"
    />
    <Main 
      :movies="movieList"
    />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Main from "./components/Main.vue";


export default {
  name: "App",
  components: {
    Main,
    Header,
  },

  data() {
    return {
      movieList: [],
      }
    },

  methods: {
    setMovieList(value) {
      this.movieList = value;
      // console.log(this.movieList);
    }
  }
};
</script>

<style lang="scss">
  @import "./assets/scss/style.scss";

  #app {
    background: $darkBgColor;
    background: linear-gradient(180deg, #060606 12%, #141414 100%);  
  }
</style>
