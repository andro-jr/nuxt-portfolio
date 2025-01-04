<template>
  <div></div>

  <section v-if="pending">Loading...</section>
  <section v-else-if="error">Loading...</section>
  <section v-else>Here is data</section>
</template>

<script setup>
const { error, pending, data } = await useFetch(
  "https://api.github.com/users/andro-jr/repos"
);
</script>
