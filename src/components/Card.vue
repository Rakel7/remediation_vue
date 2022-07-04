<template>
  <div class="card">
    <img :src="picture.large" alt="" />
    <div>{{ name.title }} {{ name.last }} {{ name.first }}</div>
    <div>{{ email }}</div>
    <div>{{ phone }}</div>
  </div>
</template>

<script>
export default {
  name: "Card",
  props: ["picture", "name", "email", "phone"],
};
</script>

<style>
</style>
