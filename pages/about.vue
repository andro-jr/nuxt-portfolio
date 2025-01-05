<template>
  <article class="prose dark:prose-invert">
    <ContentDoc path="/about" />
  </article>
</template>

<script setup>
const layout = "another";

useHead({
  title: "About",
});
</script>
