<template>
  <main>
    <section class="container">
      <h2>Film</h2>
      <ul class="row">
        <li class="col" v-for="movie in mapped_movies" :key="movie.id">
          <MovieCard :info="movie" />
        </li>
      </ul>
    </section>
    <section class="container">
      <h2>Serie TV</h2>
      <ul class="row">
        <li class="col" v-for="serie in mapped_series" :key="serie.id">
          <MovieCard :info="serie" />
        </li>
      </ul>
    </section>
  </main>
</template>

<script>
import MovieCard from './MovieCard.vue';
import state from '../store.js';

export default {
  name: 'MainContent',
  components: {
    MovieCard
  },
  data() {
    return {
      flags: {
        it: require('../assets/it-flag.png'),
        en: require('../assets/en-flag.png')
      }
    }
  },
  computed: {
    mapped_movies() {
      return state.original_movies.map((movie) => {
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
      return state.original_series.map((serie) => {
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
    getPosterPath(path) {
      if (path) {
        return `https://image.tmdb.org/t/p/w342${path}`
      }
      return null
    }
  }
}
</script>

<style scoped lang="scss">
main {
  background-color: #222;
}

h2 {
  margin-bottom: 20px;
  font-size: 3rem;
  font-weight: 700;
}

section {
  padding-top: 40px;
  padding-bottom: 40px;
  color: white;
}
</style>
