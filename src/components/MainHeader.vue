<template>
  <header>
    <h1>Boolflix</h1>
    <div>
      <input v-model="query" type="text" placeholder="Inserisci un titolo">
      <button @click="getData">Cerca</button>
    </div>
  </header>
</template>

<script>
import axios from 'axios';
import state from '../store.js'

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

      axios
        .get(`${this.BASE_URI}/search/movie`, {
          params: {
            api_key: this.api_key,
            query: this.query.trim()
          }
        })
        .then((res) => {
          console.log(res.data.results);
          state.original_movies = res.data.results;
        });

      axios
        .get(`${this.BASE_URI}/search/tv`, {
          params: {
            api_key: this.api_key,
            query: this.query.trim()
          }
        })
        .then((res) => {
          console.log(res.data.results);
          state.original_series = res.data.results;
        });
    }
  }
}
</script>

<style scoped lang="scss">
header {
  padding: 1rem 1.5rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: black;
}

h1 {
  font-weight: 400;
  text-transform: uppercase;
  color: #e50914;
}

input {
  padding: 0.5rem 0.75rem;
  border: 1px solid white;
  border-radius: 2px;
  margin-right: 1rem;
  font-size: 1rem;
  color: white;
  background-color: transparent;
}

button {
  padding: 0.5rem 0.75rem;
  border: 1px solid #e50914;
  border-radius: 2px;
  font-size: 1rem;
  background-color: #e50914;
  color: white;
}
</style>
