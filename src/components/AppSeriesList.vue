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
  <h2>SERIES:</h2>
  <!--per ogni film lista con info-->
  <ul v-for="series in store.searchedSeries" :key="series.id">
    <li>{{ series.name }}</li>
    <li>{{ series.original_name }}</li>
    <li v-if="hasFlag(series.original_language)">
      <img :src="'./img/' + series.original_language + '.png'" alt="" />
    </li>
    <li>{{ series.vote_average }}</li>
  </ul>
</template>

<style>
img {
  height: 50px;
  width: 50px;
}
</style>
