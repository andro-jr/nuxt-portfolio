<template>
  <article class="prose dark:prose-invert max-w-none">
    <ContentDoc v-slot="{ doc }">
      <div class="grid grid-cols-6 gap-16">
        <div :class="doc.toc ? 'col-span-4' : 'col-span-6'">
          <ContentRenderer :value="doc" />
        </div>
        <div class="col-span-2 not-prose" v-if="doc.toc">
          <aside class="sticky top-8">
            <div class="font-semibold mb-2">Table of Contents</div>
            <TOCLinks :links="doc.body.toc.links" :active-id="activeId" />
          </aside>
        </div>
      </div>
    </ContentDoc>
  </article>
</template>

<script setup>
let activeId = ref(null);

onMounted(() => {
  const callback = (entries) => {
    for (const entry of entries) {
      if (entry.isIntersecting) {
        activeId.value = entry.target.id;
        console.log("activeId :", activeId);
        break;
      }
    }
  };
  const observer = new IntersectionObserver(callback, {
    threshold: 0.5,
    root: null,
  });

  const elements = document.querySelectorAll("h2,h3");

  for (const element of elements) {
    observer.observe(element);
  }
  onBeforeUnmount(() => {
    for (const element of elements) {
      observer.unobserve(element);
    }
  });
});
</script>
