<template>
  <div>
    <p>{{ info.title }}</p>
    <p>{{ info.original_title }}</p>
    <p>
      <img v-if="info.lang === 'it'" src="../assets/it-flag.png" alt="">
      <img v-else-if="info.lang === 'en'" src="../assets/en-flag.png" alt="">
      <span v-else>{{ info.lang }}</span>
    </p>
    <div>
      <font-awesome-icon v-for="n in info.vote" :key="n" icon="fa-solid fa-star"></font-awesome-icon>
      <font-awesome-icon icon="fa-regular fa-star"></font-awesome-icon>
    </div>
    <img :src="info.poster" alt="info.title">
  </div>
</template>

<script>
export default {
  name: 'MovieCard',
  props: {
    info: Object,
  }
}
</script>

<style scoped>

</style>
