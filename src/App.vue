<script setup lang="ts">
import { ref, onMounted } from "vue";

import Notes from "./components/Notes.vue";
import APITests from "./components/APITests.vue";
import ScrollToElement from "./components/ScrollToElement.vue";
import BurgerMenu from "./components/BurgerMenu.vue";
import FollowingBlob from "./components/FollowingBlob.vue";
</script>

<template>
  <!-- <Notes />
  <APITests />
  <ScrollToElement /> 
  <BurgerMenu /> -->
  <FollowingBlob />
</template>

<style>
@import "./style.css";
</style>
