<template>
  <article class="prose dark:prose-invert max-w-none">
    <ContentDoc path="/about" />
  </article>
</template>

<script setup>
const layout = "another";

useHead({
  title: "About",
});
</script>
