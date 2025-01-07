<template>
  <BlogPost v-slots="{ posts }" :limit="limit">
    <div v-for="post in posts" :key="post.id">
      <NuxtLink :to="post._path"> {{ post.title }}</NuxtLink>
    </div>
  </BlogPost>
</template>

<script setup>
defineProps({
  limit: {
    type: Number,
    default: null,
  },
});
</script>
