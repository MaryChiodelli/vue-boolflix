<template>
  <div id="app">
    <MainHeader @onSearchMovies="getMovies" @onSearchSeries="getSeries" />
    <MainContent :movies="mapped_movies" :series="mapped_series" />
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
      original_movies: [],
      original_series: [],
      flags: {
        it: require('./assets/it-flag.png'),
        en: require('./assets/en-flag.png')
      }
    }
  },
  computed: {
    mapped_movies() {
      return this.original_movies.map((movie) => {
        return {
          id: movie.id,
          title: movie.title,
          original_title: movie.original_title,
          lang: movie.original_language,
          flag: this.flags[movie.original_language],
          vote: Math.ceil(movie.vote_average / 2),
          poster: this.getPosterPath(movie.poster_path)
        }
      });
    },
    mapped_series() {
      return this.original_series.map((serie) => {
        return {
          id: serie.id,
          title: serie.name,
          original_title: serie.original_name,
          lang: serie.original_language,
          flag: this.flags[serie.original_language],
          vote: Math.ceil(serie.vote_average / 2),
          poster: this.getPosterPath(serie.poster_path)
        }
      });
    }
  },
  methods: {
    getMovies(data) {
      this.original_movies = data;
    },
    getSeries(data) {
      this.original_series = data;
    },
    getPosterPath(path) {
      if (path) {
        return `https://image.tmdb.org/t/p/w342${path}`
      }
      return null
    }
  }
}
</script>

<style lang="scss">
@import url('./style/index.scss');
</style>
