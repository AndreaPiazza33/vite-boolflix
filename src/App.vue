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
  },

  /*componenti */
  components: { AppMain, AppHeader },
};
</script>

<template>
  <AppHeader @filtered-search="fetchMovie"></AppHeader>
  <AppMain></AppMain>
</template>

<style lang="scss"></style>
