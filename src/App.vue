<template>
  <div id="app">
    {{movies}}
    <MainHeader @onSearch="getMovies" />
    <MainContent :movies="movies" />
  </div>
</template>

<script>
import MainHeader from './components/MainHeader.vue';
import MainContent from './components/MainContent.vue';

export default {
  name: 'App',
  components: {
    MainHeader,
    MainContent
  },
  data() {
    return {
      movies: []
    }
  },
  methods: {
    getMovies(data) {
      this.movies = data;
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
