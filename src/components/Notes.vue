<script setup lang="ts">
const notes = ["Test", "Test1", "Test2"];
</script>

<template>
  <div class="text-2xl" v-for="note in notes">{{ note }}</div>
</template>
