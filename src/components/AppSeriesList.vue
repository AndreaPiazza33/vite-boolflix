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
  <h2>SERIES:</h2>
  <!--per ogni film lista con info-->
  <ul v-for="series in store.searchedSeries" :key="series.id">
    <img
      :src="posterUrl.baseUrl + posterUrl.size + series.poster_path"
      alt=""
    />
    <li>{{ series.name }}</li>
    <li>{{ series.original_name }}</li>
    <li v-if="hasFlag(series.original_language)">
      <img
        class="img-size"
        :src="'./img/' + series.original_language + '.png'"
        alt=""
      />
    </li>
    <li>{{ series.vote_average }}</li>
  </ul>
</template>

<style>
.img-size {
  height: 20px;
  width: 20px;
}
</style>
