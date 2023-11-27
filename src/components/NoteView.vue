<template>
    <div id="note-view">
      <h3>{{ selectedNote.title }}</h3>
      <p>{{ selectedNote.content }}</p>
      <button @click="newNote">New</button>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      selectedNote: Object,
    },
    methods: {
      newNote() {
        this.$emit("new-click");
      },
    },
  };
  </script>

  