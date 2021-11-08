<template>
  <h4 v-for="feat in filteredFeats" :key="feat.name">{{ feat.name }}</h4>
</template>

<script>
import data from "../assets/data.json";

export default {
  name: "App",
  components: {},
  props: ["searchWord"],
  data() {
    return {
      allFeats: [],
      filteredFeats: [],
    };
  },
  updated() {
    this.filterFeats();
  },
  mounted() {
    this.allFeats = data.feats;

    this.filterFeats();
  },
  methods: {
    filterFeats() {
      this.filteredFeats = this.allFeats.filter(
        (feat) =>
          feat.name.toLowerCase().includes(this.searchWord.toLowerCase()) ||
          feat.desc.toLowerCase().includes(this.searchWord.toLowerCase())
      );
    },
  },
};
</script>

<style scoped>
</style>