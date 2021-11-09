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
    <h1>{{ feat.name }}</h1>
    <p v-if="feat.prerequisite" class="fs-5 fst-italic">
      Required: {{ feat.prerequisite }}
    </p>
    <p class="fs-5">{{ feat.desc }}</p>
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
  padding: 30px;
  width: 25%;
  border-radius: 20px;
}
</style>