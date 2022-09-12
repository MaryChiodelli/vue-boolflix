<template>
  <div>
    <p>{{ info.title }}</p>
    <p>{{ info.original_title }}</p>
    <p>
      <img v-if="info.lang === 'it'" src="../assets/it-flag.png" alt="">
      <img v-else-if="info.lang === 'en'" src="../assets/en-flag.png" alt="">
      <span v-else>{{ info.lang }}</span>
    </p>
    <p>{{ info.vote }}</p>
    <img :src="info.poster" alt="info.title">
  </div>
</template>

<script>
export default {
  name: 'MovieCard',
  props: {
    info: Object
  }
}
</script>

<style scoped>

</style>
