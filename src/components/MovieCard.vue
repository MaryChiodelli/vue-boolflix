<template>
  <div class="card">
     <img :src="info.poster" alt="info.title">
    <div class="card-content">
      <p>{{ info.title }}</p>
      <p>{{ info.original_title }}</p>
      <p>
        <img v-if="info.lang === 'it'" src="../assets/it-flag.png" alt="">
        <img v-else-if="info.lang === 'en'" src="../assets/en-flag.png" alt="">
        <span v-else>{{ info.lang }}</span>
      </p>
      <div>
        <font-awesome-icon v-for="n in info.vote" :key="n" icon="fa-solid fa-star"></font-awesome-icon>
        <font-awesome-icon v-for="n in 5 - info.vote" :key="5 + n" icon="fa-regular fa-star"></font-awesome-icon>
      </div>
    </div>
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

<style lang="scss" scoped>
.card {
  height: 100%;
  position: relative;

  img {
    display: block;
    width: 100%;
    height: 100%;
    object-fit: cover;

    &::after {
      contain: '';
      position: absolute;
      top: 0;
      right: 0;
      bottom: 0;
      left: 0;
      opacity: 0;
      background-color: rgba(0, 0, 0, 1);
    }
  }

  .card-content {
    padding: 20px;
    position: absolute;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    opacity: 0;

    &:hover {
      opacity: 1;
    }
  }
}
</style>
