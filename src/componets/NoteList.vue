<script setup>
import { ref } from "vue";
import CreateNote from "./CreateNote.vue";
const notes = ref([]);

// getnotes with a fetch and make note list

function getNotes () {
    fetch("http://localhost:3000/notes/", {
      method: "GET",
      headers: { "Content-Type": "application/json" }
    })
      .then((r) => r.json())
      .then((data) =>(notes.value = data) )
    };

  const addNote = (note) => {
  notes.value = [...notes.value, note];
  };

  getNotes();
</script>


<template>
  <div id="noteHolder">
    <CreateNote />
    <div class="noteCard" v-for="note in notes" :key="note.id">
    <h3>{{  note.title }}</h3>
    <p>{{ note.body }}</p>
    
  </div>
  </div>
</template>