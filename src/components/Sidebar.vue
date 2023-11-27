<template>
    <div id="sidebar">
      <h2>Your Notes</h2>
      <div v-for="(note, index) in savedNotes" :key="index" class="note" @click="selectNote(index)">
        <strong>Note {{ index + 1 }}:</strong> {{ note.title }}
        <span class="delete-note" @click="deleteNote(index)">×</span>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      savedNotes: Array,
    },
    methods: {
      selectNote(index) {
        this.$emit("note-click", index);
      },
      deleteNote(index) {
        console.log("Delete clicked")
        this.$emit("delete-click", index);
      },
    },
  };
  </script>
  
  