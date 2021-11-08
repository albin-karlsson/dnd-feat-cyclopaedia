<template>
  <div v-for="feat in filteredFeats" :key="feat.name">
    <h4 v-html="highlight(feat.name)"></h4>
    <p>{{ feat.desc }}</p>
  </div>
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
    this.filteredFeats = this.allFeats;
  },
  methods: {
    filterFeats() {
      let words = this.searchWord.split(" ").map((word) => word.toLowerCase());

      words.forEach((word) => {
        this.filteredFeats = this.allFeats.filter(
          (feat) =>
            feat.name.toLowerCase().includes(word) ||
            feat.desc.toLowerCase().includes(word)
        );
      });
    },
    highlight(text) {
      if (!this.searchWord) {
        return text;
      } else {
        return text.replace(new RegExp(this.searchWord, "gi"), (match) => {
          return '<span class="highlighted">' + match + "</span>";
        });
      }
    },
  },
};
</script>

<style>
.highlighted {
  background-color: blanchedalmond;
}
</style>