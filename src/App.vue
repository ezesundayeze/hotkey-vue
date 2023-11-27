<template>
  <div id="app">
    <NotesApp />
  </div>
</template>

<script>
import NotesApp from "./components/NotesApp.vue";

export default {
  components: {
    NotesApp,
  },
};
</script>

<style>
body {
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  margin: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100vh;
  /* background-color: #f7f9fc; */
}
</style>
