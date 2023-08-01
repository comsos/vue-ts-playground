<script setup lang="ts">
import { ref, onMounted } from "vue";

const hero = ref<HTMLElement | null>(null);
const second = ref<HTMLElement | null>(null);

const scrollToElement = (scrollTarget: HTMLElement | null) => {
  if (scrollTarget) {
    scrollTarget.scrollIntoView({ behavior: "smooth" });
  }
};

// Run the scrollToElement function when the component is mounted
onMounted(() => scrollToElement(hero.value));
</script>

<template>
  <div class="sticky top-0">
    <button @click="scrollToElement(hero)">Main</button>
    <button @click="scrollToElement(second)">Second</button>
  </div>
  <div class="h-screen w-full bg-red-500" ref="hero"></div>
  <div class="h-screen w-full bg-blue-500" ref="second"></div>
</template>
