<template>
  <slot :posts="posts">
    <section class="not-prose font-mono">
      <div class="column tex-gray-400 text-sm">
        <div>date</div>
        <div>title</div>
      </div>
      <ul>
        <li v-for="post in posts" :key="post._path">
          <NuxtLink
            :href="post._path"
            class="column hover:bg-gray-100 dark:hover:bg-gray-800"
          >
            <div class="text-gray-500 min-w-10">
              {{ post.displayYear ? post.year : "" }}
            </div>
            <div>
              {{ post.title }}
            </div>
          </NuxtLink>
        </li>
      </ul>
    </section>
  </slot>
</template>

<script setup>
const props = defineProps({
  limit: {
    type: Number,
    default: 0,
  },
});

const { data } = await useAsyncData("blog-list", () => {
  const query = queryContent("/blog")
    .where({ _path: { $ne: "/blog" } })
    .only(["_path", "title", "publishedAt"])
    .sort({ publishedAt: -1 });

  if (props.limit) query.limit(props.limit);

  return query.find();
});

const posts = computed(() => {
  if (!data.value) {
    return [];
  }
  const result = [];
  let lastYear = null;
  for (const post of data.value) {
    const year = new Date(post.publishedAt).getFullYear();
    const displayYear = year !== lastYear;
    post.displayYear = displayYear;
    post.year = year;
    result.push(post);
    lastYear = year;
  }
  console.log("result :", result);
  return result;
});
</script>

<style scoped>
.column {
  @apply flex items-center space-x-8 py-2 border-b border-gray-200 dark:border-gray-700;
}
</style>
