<template>
  <div v-for="feat in filteredFeats" :key="feat.name">
    <h4 v-html="highlight(feat.name)"></h4>
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

    this.filterFeats();
  },
  methods: {
    filterFeats() {
      this.filteredFeats = this.allFeats.filter(
        (feat) =>
          feat.name
            .toLowerCase()
            .includes(this.searchWord.trim().toLowerCase()) ||
          feat.desc.toLowerCase().includes(this.searchWord.trim().toLowerCase())
      );
    },
    highlight(featName) {
      if (!this.searchWord) {
        return featName;
      } else {
        return featName.replace(new RegExp(this.searchWord, "gi"), (match) => {
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