<template>
  <SearchBar />
  <List />
</template>

<script>
import SearchBar from "./components/SearchBar.vue";
import List from "./components/List.vue";

export default {
  name: "App",
  components: {
    SearchBar,
    List,
  },
};
</script>

<style>
</style>
