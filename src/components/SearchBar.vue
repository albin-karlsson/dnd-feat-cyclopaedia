<template>
  <input
    class="form-control mb-5"
    type="text"
    placeholder="Search feat..."
    v-model="searchWord"
    @input="addInput"
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
      this.$emit("inputAdded", this.searchWord);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>