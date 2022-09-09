<template>
  <header>
    <input v-model="query" type="text">
    <button>cerca</button>
  </header>
</template>

<script>
import axios from 'axios';

export default {
  name: 'MainHeader',
  data() {
    return {
      BASE_URI: 'https://api.themoviedb.org/3',
      api_key: '735e75087705e688a8302c51505637e4',
      query: 'ritorno',
      // movies: []
    }
  },
  methods: {
    fetchMovies() {
      axios
        .get(`${this.BASE_URI}/search/movie?api_key=${this.api_key}&query=${this.query}`)
        .then(((res) => {
          console.log(res.data.results);
        }));
    }
  },
  created() {
    this.fetchMovies();
  }
}
</script>

<style scoped lang="scss">

</style>
