<template>
  <main>
    <h2>Movies: {{movies.length}}</h2>
    <ul>
      <li v-for="movie in movies" :key="movie.id">
        <MovieCard :info="movie" />
      </li>
    </ul>
    <h2>Series: {{series.length}}</h2>
    <ul>
      <li v-for="serie in series" :key="serie.id">
        <MovieCard :info="serie" />
      </li>
    </ul>
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

</style>
