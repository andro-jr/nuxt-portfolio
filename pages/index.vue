<template>
  <div>This is main page!</div>
</template>

<script setup>
useSeoMeta({
  title: "Main Page",
  description: "This is main page",
  ogTitle: "Main Page",
  ogDescription: "This is main page",
});

useHead({
  htmlAttrs: {
    lang: "en",
  },
  link: [
    {
      rel: "icon",
      type: "image/png",
      href: "/favicon.png",
    },
  ],
});
</script>
