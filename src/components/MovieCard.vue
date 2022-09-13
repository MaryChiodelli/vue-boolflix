<template>
  <div class="card">
    <img class="poster" v-if="info.poster" :src="info.poster" alt="info.title">
    <div class="placeholder" v-else></div>

    <div class="card-content">
      <h3 class="title">{{ info.title }}</h3>
      <p class="original-title">{{ info.original_title }}</p>

      <img class="flag" v-if="info.flag" :src="info.flag" alt="">
      <div class="lang" v-else>{{ info.lang }}</div>

      <div class="stars">
        <font-awesome-icon v-for="n in info.vote" :key="n" icon="fa-solid fa-star"></font-awesome-icon>
        <font-awesome-icon v-for="n in (5 - info.vote)" :key="n + info.vote" icon="fa-regular fa-star"></font-awesome-icon>
      </div>

      <button @click="getCastInfo">Altre info</button>
      <p>{{castList}}</p>
      <p>{{genreList}}</p>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'MovieCard',
  props: {
    info: Object,
  },
  data() {
    return {
      BASE_URI: 'https://api.themoviedb.org/3',
      api_key: '735e75087705e688a8302c51505637e4',
      genres: [],
      cast: []
    }
  },
  computed: {
    genreList() {
      let genreArray = []
      this.genres.forEach((el) => {
        genreArray.push(el.name);
      });
      return genreArray.join(', ');
    },
    castList() {
      let names = [];
      this.cast.forEach((el, i) => {
        if (i < 5) {
          names.push(el.name);
        }
      })
      return names.join(', ')
    }
  },
  methods: {
    getCastInfo() {
      this.fetchGenres();
      this.fetchCast();
    },
    fetchGenres() {
      axios
        .get(`${this.BASE_URI}/movie/${this.info.id}`, {
          params: {
            api_key: this.api_key
          }
        })
        .then((res) => {
          console.log(res.data.genres);
          this.genres = res.data.genres;
        });
    },
    fetchCast() {
      axios
        .get(`${this.BASE_URI}/movie/${this.info.id}/credits`, {
          params: {
            api_key: this.api_key
          }
        })
        .then((res) => {
          console.log(res.data.cast);
          this.cast = res.data.cast;
        });
    }
  }
}
</script>

<style lang="scss" scoped>
.card {
  height: 100%;
  position: relative;

  .poster {
    display: block;
    width: 100%;
    height: 100%;
    object-fit: cover;
  }

  .placeholder {
    height: 100%;
    border: 8px solid black;
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
      background-color: black;
    }
  }

  .flag {
    width: 40px;
  }

  .stars * {
    margin-right: 0.25rem;
  }
}
</style>
