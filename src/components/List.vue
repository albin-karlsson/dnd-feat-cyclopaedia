<template>
  <div
    v-for="feat in filteredFeats"
    :key="feat.name"
    @mouseover="displayDetails(feat)"
    @mouseout="hideDetails"
  >
    <h4 v-html="highlight(feat.name)"></h4>
    <p v-if="feat.prerequisite" class="fst-italic">
      Required: <span v-html="highlight(feat.prerequisite)"></span>
    </p>
    <p v-html="highlight(feat.desc)"></p>
  </div>
  <Details v-if="showDetails" :feat="detailedFeat" />
</template>

<script>
import data from "../assets/data.json";
import Details from "../components/Details.vue";

export default {
  name: "List",
  components: { Details },
  props: ["searchWord"],
  data() {
    return {
      allFeats: [],
      filteredFeats: [],
      showDetails: false,
      detailedFeat: {},
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
      if (this.searchWord) {
        let words = this.searchWord
          .split(" ")
          .filter((word) => word != "")
          .map((word) => word.toLowerCase());

        words.forEach((word) => {
          this.filteredFeats = this.allFeats.filter(
            (feat) =>
              feat.name.toLowerCase().includes(word) ||
              feat.desc.toLowerCase().includes(word) ||
              (typeof feat.prerequisite !== "undefined" &&
                feat.prerequisite.toLowerCase().includes(word))
          );
        });
      } else {
        this.filteredFeats = this.allFeats;
      }
    },
    highlight(text) {
      if (!this.searchWord) {
        return text;
      } else {
        // let words = this.searchWord
        //   .split(" ")
        //   .filter((word) => word != "")
        //   .map((word) => word.toLowerCase());

        // let html;

        // words.forEach(
        //   (word) =>
        //     (html = text.replace(new RegExp(word, "gi"), (match) => {
        //       '<span class="highlighted">' + match + "</span>";
        //     }))
        // );

        // return text;

        return text.replaceAll(new RegExp(this.searchWord, "gi"), (match) => {
          return '<span class="highlighted">' + match + "</span>";
        });
      }
    },
    displayDetails(feat) {
      this.showDetails = true;
      this.detailedFeat = feat;
    },
    hideDetails() {
      this.showDetails = false;
    },
  },
};
</script>

<style>
.highlighted {
  background-color: blanchedalmond;
}
</style>