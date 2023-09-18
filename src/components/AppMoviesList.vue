<script>
import { store } from "../store";
export default {
  data() {
    return {
      store,
      posterUrl: {
        baseUrl: "https://image.tmdb.org/t/p/",
        size: "/w342",
      },
    };
  },
  methods: {
    hasFlag(language) {
      const allowedFlag = ["en", "it"];
      return allowedFlag.includes(language);
    },
  },
};
</script>

<template>
  <h2>MOVIES:</h2>
  <!--per ogni film lista con info-->
  <ul v-for="movie in store.searchedMovie" :key="movie.id">
    <img :src="posterUrl.baseUrl + posterUrl.size + movie.poster_path" alt="" />
    <li>{{ movie.title }}</li>
    <li>{{ movie.original_title }}</li>
    <li v-if="hasFlag(movie.original_language)">
      <img
        class="img-size"
        :src="'./img/' + movie.original_language + '.png'"
        alt=""
      />
    </li>
    <li>{{ movie.vote_average }}</li>
  </ul>
</template>

<style>
.img-size {
  height: 20px;
  width: 20px;
}
</style>
