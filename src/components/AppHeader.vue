<script>
export default {
  data() {
    return {
      search: "",
    };
  },
  emits: ["filtered-search"],
};
</script>

<template>
  <!--titolo-->
  <div>BOOLFLIX</div>
  <!--searchbar-->
  <div>
    <form role="search" @submit.prevent="$emit('filtered-search', search)">
      <input type="search" placeholder="Search a movie" v-model="search" />
      <button type="submit">Search</button>
    </form>
  </div>
</template>

<style></style>
