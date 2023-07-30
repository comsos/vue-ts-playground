<script setup lang="ts">
import { ref } from "vue";

const newNote = ref("");

const noteIs = ref(false);

type Note = {
  note: string;
  done: boolean;
  date: number;
};

const currentDate = new Date();
const timestamp = currentDate.getTime();

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
        notes.push({ note: newNote, done: false, date: timestamp });
        newNote = '';
      }
    "
    @keydown="
      () => {
        console.log(noteIs);
        console.log(newNote);
        noteIs = true;
      }
    "
  />
  <button
    @click="
      () => {
        notes.push({ note: newNote, done: false, date: timestamp });
        newNote = '';
        noteIs = false;
      }
    "
    :class="[newNote ? 'visible' : 'invisible']"
  >
    Test
  </button>
  <div class="text-2xl flex flex-row" v-for="(note, index) in notes">
    <input type="checkbox" v-model="note.done" />
    <p v-bind:id="`${index}`" :class="{ 'line-through': note.done }">
      {{ index + 1 }} {{ note.note }}
    </p>
    <button @click="removeNote(note)">X</button>
  </div>
</template>
