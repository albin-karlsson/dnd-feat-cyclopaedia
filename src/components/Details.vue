<template>
  <div
    class="
      position-fixed position-absolute
      top-50
      end-0
      translate-middle-y
      m-5
      background
    "
  >
    <h2>{{ feat.name }}</h2>
    <p v-if="feat.prerequisite" class="fst-italic">
      Required: {{ feat.prerequisite }}
    </p>
    <p>{{ feat.desc }}</p>
  </div>
</template>

<script>
export default {
  name: "Details",
  props: ["feat"],
};
</script>
<style>
.background {
  background-color: blanchedalmond;
  padding: 10px;
  width: 25%;
}
</style>