<template>
  <SearchBar @inputAdded="logSearchWord" />
  <List :searchWord="searchWord" />
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
  data() {
    return {
      searchWord: "",
    };
  },
  methods: {
    logSearchWord(searchWord) {
      this.searchWord = searchWord;
    },
  },
};
</script>

<style>
</style>
