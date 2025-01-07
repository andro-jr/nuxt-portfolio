<template>
  <NuxtLayout>
    <section>
      <h1>OOPS! {{ error.status }}</h1>
      <h2>{{ error.statusMessage }}</h2>
    </section>
  </NuxtLayout>
</template>

<script setup>
defineProps({
  error: Object,
});
</script>
