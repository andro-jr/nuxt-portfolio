<template>
  <div class="flex space-x-2 items-center">
    <div class="text-gray-500 text-xs" v-if="showNextModeLabel">
      Change to {{ nextMode }}
    </div>
    <button
      @mouseenter="showNextModeLabel = true"
      @mouseleave="showNextModeLabel = false"
      @click="toggleMode"
    >
      {{ nextModeIcon }}
    </button>
  </div>
</template>

<script setup>
const colorMode = useColorMode();

const showNextModeLabel = ref(false);

const modes = ["system", "light", "dark"];

const nextModeIcons = {
  system: "🌓",
  light: "🌕",
  dark: "🌑",
};

const nextMode = computed(() => {
  const currentModeIndex = modes.indexOf(colorMode.preference);

  let nextModeIndex = null;
  if (currentModeIndex + 1 === modes.length) {
    nextModeIndex = 0;
  } else {
    nextModeIndex = currentModeIndex + 1;
  }

  return modes[nextModeIndex];
});

const nextModeIcon = computed(() => nextModeIcons[nextMode.value]);

const toggleMode = () => {
  colorMode.preference = nextMode.value;
};
</script>
