<template>
    <div id="note-edit">

        <h3>Edit Note</h3>
        <label for="title-input">Title:</label>
        <input type="text" id="title-input" placeholder="Enter note title" v-model="editedNote.title">
        <textarea id="edit-text" rows="4" placeholder="Enter note content" v-model="editedNote.content"
            data-hotkey="Control+s"
            ></textarea>
        <button @click="saveNote" data-hotkey="Control+s">Save</button>
    </div>
</template>
  
<script>
import { install } from '@github/hotkey';

export default {
    props: {
        editedNote: Object,
    },
    methods: {
        saveNote(e) {
            e.preventDefault();
            this.$emit("save-click");
        },
        hotkeyFired(e) {
            e.preventDefault();
            if(e.ctrlKey==true && e.key=="s"){
                this.$emit("save-click");

            }
        },
        mount() {
            for (const el of document.querySelectorAll('[data-hotkey]')) {
                install(el, el.dataset.hotkey);
            }
        },
    },
    mounted() {
        this.mount(); // Call the mount method when the component is mounted
    },
};
</script>
  