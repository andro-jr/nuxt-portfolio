<template>
  <div>We are inside blogs page</div>
  <div>The post id is {{ route.params.id }}</div>
</template>

<script setup>
const route = useRoute();
</script>
