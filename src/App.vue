<template>
  <h1 class="display-2 text-center mb-5">Feat Cyclopaedia</h1>
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
#app {
  margin: 5% 20%;
}
</style>
