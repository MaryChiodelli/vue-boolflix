<template>
  <main>
    <h2>Movies: {{movies.length}}</h2>
    <ul>
      <li v-for="movie in movies" :key="movie.id">
        <p>{{ movie.title }}</p>
        <p>{{ movie.original_title }}</p>
        <p>
          <img v-if="movie.original_language === 'it'" src="../assets/it-flag.png" alt="">
          <img v-else-if="movie.original_language === 'en'" src="../assets/en-flag.png" alt="">
          <span v-else>{{ movie.original_language }}</span>
        </p>
        <p>{{ movie.vote_average }}</p>
      </li>
    </ul>
    <h2>Series: {{series.length}}</h2>
    <ul>
      <li v-for="serie in series" :key="serie.id">
        <p>{{ serie.name }}</p>
        <p>{{ serie.original_name }}</p>
        <p>
          <img v-if="serie.original_language === 'it'" src="../assets/it-flag.png" alt="">
          <img v-else-if="serie.original_language === 'en'" src="../assets/en-flag.png" alt="">
          <span v-else>{{ serie.original_language }}</span>
        </p>
        <p>{{ serie.vote_average }}</p>
      </li>
    </ul>
  </main>
</template>

<script>
export default {
  name: 'MainContent',
  props: {
    movies: Array,
    series: Array
  }
}
</script>

<style scoped lang="scss">

</style>
