<script setup lang="ts">
import axios from "axios";
import { ref } from "vue";

type Question = {
  strCategory: string;
  strArea: string;
};

// const questions = ref<Array<Question>>([]);
const questions = ref<Array<Question>>([]);

const fetchQuestions = (url: string, type: string) => {
  axios
    .get(url)
    .then((response) => {
      questions.value = response.data.meals;
      console.log(response.data.meals);
    })
    .catch((error) => {
      console.error("Error fetching questions:", error);
    });
};
</script>

<template>
  <button
    @click="
      fetchQuestions(
        'https://www.themealdb.com/api/json/v1/1/categories.php',
        'categories'
      )
    "
  >
    Categories
  </button>
  <button
    @click="
      fetchQuestions(
        'https://www.themealdb.com/api/json/v1/1/list.php?a=list',
        'area'
      )
    "
  >
    Area
  </button>
  <div v-for="question in questions" class="text-xl">
    <a
      :href="`${'https://www.themealdb.com/api/json/v1/1/filter.php?a='}${
        question.strArea
      }`"
      target="_blank"
      class="hover:text-blue-700"
    >
      {{ question.strArea }}
    </a>
  </div>
</template>
