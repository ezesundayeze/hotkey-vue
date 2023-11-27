<template>
    <Sidebar :savedNotes="savedNotes" @note-click="toggleNoteView" @delete-click="deleteNote" />
    <NoteView
      v-if="isNoteViewVisible"
      :selectedNote="selectedNote"
      @new-click="toggleNoteView"
    />
    <NoteEdit
      v-else
      :editedNote="editedNote"
      @save-click="saveNote"
    />
</template>

<script>
import Sidebar from "./Sidebar.vue";
import NoteView from "./NoteView.vue";
import NoteEdit from "./NoteEdit.vue";


export default {
  data() {
    return {
      savedNotes: JSON.parse(localStorage.getItem("notes")) || [],
      selectedNote: { title: "", content: "" },
      editedNote: { title: "", content: "" },
      isNoteViewVisible: false,
    };
  },
  methods: {
    toggleNoteView(index = null) {
      if (index !== null) {
        this.selectedNote = this.savedNotes[index];
      }
      this.isNoteViewVisible = !this.isNoteViewVisible;
      this.editedNote = { title: "", content: "" };
    },
    deleteNote(index) {
      if (confirm("Are you sure you want to delete this note?")) {
        this.savedNotes.splice(index, 1);
        localStorage.setItem("notes", JSON.stringify(this.savedNotes));
        this.toggleNoteView();
      }
    },
    saveNote() {
      const { title, content } = this.editedNote;
      if (title && content) {
        const newNote = { title, content };
        this.savedNotes.push(newNote);
        localStorage.setItem("notes", JSON.stringify(this.savedNotes));
        this.toggleNoteView();
        alert(`Note saved with title: ${title}`);
      } else {
        alert("Please enter both title and content before saving.");
      }
    },
  },
  components: {
    Sidebar,
    NoteView,
    NoteEdit,
  },
};
</script>

