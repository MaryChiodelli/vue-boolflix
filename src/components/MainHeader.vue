<template>
  <header>
    <input v-model="query" type="text" placeholder="Inserisci un titolo">
    <button @click="getData">cerca</button>
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
      query: ''
    }
  },
  methods: {
    getData() {
      if (!this.query.trim()) {
        return
      }

      this.fetchMovies();
      this.fetchSeries();
    },
    fetchMovies() {
      axios
        .get(`${this.BASE_URI}/search/movie`, {
          params: {
            api_key: this.api_key,
            query: this.query.trim()
          }
        })
        .then((res) => {
          console.log(res.data.results);
          this.$emit('onSearchMovies', res.data.results);
        });
    },
    fetchSeries() {
      axios
        .get(`${this.BASE_URI}/search/tv`, {
          params: {
            api_key: this.api_key,
            query: this.query.trim()
          }
        })
        .then((res) => {
          console.log(res.data.results);
          this.$emit('onSearchSeries', res.data.results);
        });
    }
  }
}
</script>

<style scoped lang="scss">

</style>
