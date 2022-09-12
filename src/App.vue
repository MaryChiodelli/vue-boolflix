<template>
  <div id="app">
    <MainHeader @onSearchMovies="getMovies" @onSearchSeries="getSeries" />
    <MainContent :movies="movies" :series="series" />
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
      movies: [],
      series: []
    }
  },
  methods: {
    getMovies(data) {
      this.movies = data;
    },
    getSeries(data) {
      this.series = data;
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
