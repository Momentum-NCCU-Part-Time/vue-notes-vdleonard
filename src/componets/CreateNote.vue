<script setup>
import { ref } from "vue";
const newNoteTitle = ref("");
const newNoteBody = ref("");



const createNote =() => {
  fetch("http://localhost:3000/notes/", {
    method: "POST",
    headers: {"Content-Type": "application/json"},
    body: JSON.stringify({ title: newNoteTitle.value, body: newNoteBody.value }),
}) 
then((res) => res.json())
  .then((note) => {
   // did generate html last project, not sure what to do here for vue instead.
  })

}
</script>

<template>
  <!-- form for create --> 

<form id="newNote">
  <h3> Create a New Note</h3>
  <div class="title">
    <input type="text" v-model="newNoteTitle" placeholder="Title">
  </div>
  <div class="body">
    <textarea type="text" v-model="newNoteBody" rows="3" cols="17" placeholder="enter note here..."></textarea>
  </div>
  <button type="submit"> Save </button>
</form>

</template>