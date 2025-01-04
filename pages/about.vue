<template>
  <NuxtLayout :name="layout">
    <div>This is about page</div>
  </NuxtLayout>
</template>

<script setup>
const layout = "another";

useHead({
  title: "About",
});
</script>
