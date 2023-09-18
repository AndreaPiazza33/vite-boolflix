<script>
import { store } from "../store";
export default {
  data() {
    return {
      store,
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
  <!--per ogni film lista con info-->
  <ul v-for="movie in store.searchedMovie" :key="movie.id">
    <li>{{ movie.title }}</li>
    <li>{{ movie.original_title }}</li>
    <li v-if="hasFlag(movie.original_language)">
      <img :src="'./img/' + movie.original_language + '.png'" alt="" />
    </li>
    <li>{{ movie.vote_average }}</li>
  </ul>
</template>

<style>
img {
  height: 100px;
  width: 100px;
}
</style>
