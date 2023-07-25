<script setup lang="ts">
import { ref } from "vue";

const newNote = ref("");

type Note = {
  note: string;
  done: boolean;
  date: string;
};

const notes = ref<Array<Note>>([]);

function removeNote(note: Object) {
  notes.value = notes.value.filter((t) => t !== note);
}
</script>

<template>
  <input
    v-model="newNote"
    @keyup.enter="
      () => {
        notes.push({ note: newNote, done: false, date: Date() });
        newNote = '';
      }
    "
  />
  <button
    @click="
      () => {
        notes.push({ note: newNote, done: false, date: Date() });
        newNote = '';
      }
    "
  >
    Test
  </button>
  <div class="text-2xl flex flex-row" v-for="(note, index) in notes">
    <p v-bind:id="`${index}`">{{ index + 1 }} {{ note.note }}</p>
    <button @click="removeNote(note)">X</button>
  </div>
</template>
