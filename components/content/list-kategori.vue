<template>
  <select>
    <option>{{ nama }}</option>
  </select>
</template>

<script>
export default {
  props: {
    nama: {
      type: String,
      default: ""
    }
  }
};
</script>

<style></style>
