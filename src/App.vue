<script>
import axios from "axios";
import { store } from "./store";
import AppMain from "./components/AppMain.vue";
import AppHeader from "./components/AppHeader.vue";

export default {
  data() {
    return {
      store,
    };
  },
  methods: {
    /*chiamata film*/
    fetchMovie(queryString) {
      axios
        .get("https://api.themoviedb.org/3/search/movie?", {
          /*parametri della chiamata*/
          params: {
            query: queryString,
            api_key: "e20fa320327eeb0c5e15c0385a71f9e5",
          },
        })
        .then((response) => {
          /*info utili del film*/
          const moviesData = response.data.results.map((searchedMovie) => {
            const { title, original_title, original_language, vote_average } =
              searchedMovie;
            return { title, original_title, original_language, vote_average };
          });
          store.searchedMovie = moviesData;
        });
    },
    fetchSeries(queryString) {
      axios
        .get("https://api.themoviedb.org/3/search/tv?", {
          params: {
            query: queryString,
            api_key: "e20fa320327eeb0c5e15c0385a71f9e5",
          },
        })
        .then((response) => {
          const seriesData = response.data.results.map((searchedSeries) => {
            const { name, original_name, original_language, vote_average } =
              searchedSeries;
            return { name, original_name, original_language, vote_average };
          });
          store.searchedSeries = seriesData;
        });
    },
    handleSearch(querystring) {
      this.fetchMovie(querystring);
      this.fetchSeries(querystring);
    },
  },

  /*componenti */
  components: { AppMain, AppHeader },
};
</script>

<template>
  <AppHeader @filtered-search="handleSearch"></AppHeader>
  <AppMain></AppMain>
</template>

<style lang="scss"></style>
