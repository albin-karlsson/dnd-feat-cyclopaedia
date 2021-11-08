<template>
  <input
    type="text"
    placeholder="Search feat..."
    v-model="searchWord"
    @change="addInput"
  />
</template>

<script>
export default {
  name: "SearchBar",
  data() {
    return {
      searchWord: "",
    };
  },
  methods: {
    addInput(event) {
      // this.$emit("inputAdded", this.searchWord);
      console.log(this.searchWord);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>