<template>
  <h4 v-for="feat in feats" :key="feat.name">{{ feat.name }}</h4>
</template>

<script>
import data from "../assets/data.json";

export default {
  name: "App",
  components: {},
  data() {
    return {
      feats: [],
    };
  },
  mounted() {
    this.feats = data.feats;
  },
};
</script>

<style scoped>
</style>