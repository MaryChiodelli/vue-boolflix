<template>
  <main>
    <section class="container">
      <h2>Film</h2>
      <ul class="row">
        <li class="col" v-for="movie in movies" :key="movie.id">
          <MovieCard :info="movie" />
        </li>
      </ul>
    </section>
    <section class="container">
      <h2>Serie TV</h2>
      <ul class="row">
        <li class="col" v-for="serie in series" :key="serie.id">
          <MovieCard :info="serie" />
        </li>
      </ul>
    </section>
  </main>
</template>

<script>
import MovieCard from './MovieCard.vue';

export default {
  name: 'MainContent',
  components: {
    MovieCard
  },
  props: {
    movies: Array,
    series: Array
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
