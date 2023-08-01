<script setup lang="ts">
import { ref } from "vue";

const x = ref<number>(0);
const y = ref<number>(0);

const blob = ref<HTMLElement | null>(null);
</script>

<template>
  <div
    style="
      background-color: black;
      height: 100vh;
      margin: 0rem;
      overflow: hidden;
    "
    @mousemove="
      (event) => {
        x = event.clientX;
        y = event.clientY;
        console.log(x, y);
        blob?.animate(
          {
            left: x + 'px',
            top: y + 'px',
          },
          { duration: 3000 }
        );
      }
    "
  >
    <div class="blur-[12vmax]">
      <div
        class="bg-gradient-to-r from-indigo-500 via-purple-500 to-pink-500 h-96 aspect-square absolute x-[50%] y-[50%] -translate-x-[50%] -translate-y-[50%] rounded-full"
        ref="blob"
      />
    </div>
  </div>
</template>
