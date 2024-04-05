<script setup>
  import { ref } from "vue";

  import Note from "@/components/notes/Note.vue";

  const newNote = ref('');
  const newNoteRef = ref(null);
  const notes = ref([
    {
      id: 'id1',
      content: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit. Ea hic ipsum maxime' +
          ' necessitatibus nemo nihil odit quasi, temporibus voluptas voluptatem!',
    },
    {
      id: 'id2',
      content: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit. Ea hic ipsum maxime',
    },
    {
      id: 'id3',
      content: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit. Ea hic ipsum maxime' +
          ' necessitatibus nemo nihil odit quasi, temporibus voluptas voluptatem!' +
          ' necessitatibus nemo nihil odit quasi, temporibus voluptas voluptatem!',
    }
  ]);

  const addNewNote = () => {
    let currentDate = new Date().getTime();
    let id = currentDate.toString();

    let note = {
      id: id,
      content: newNote.value,
    }

    notes.value.unshift(note);
    newNote.value = '';
    newNoteRef.value.focus();
  }

  const deleteThisNote = (id) => {
    notes.value = notes.value.filter(note => {
      return note.id !== id;
    })
  }

</script>

<template>
  <div class="notes">
    <div class="card has-background-success-dark p-4 mb-5">
      <div class="field">
        <div class="control">
          <textarea
            v-model="newNote"
            class="textarea"
            placeholder="Add a new note"
            ref="newNoteRef"
          ></textarea>
        </div>
      </div>

      <div class="field is-grouped is-grouped-right">
        <div class="control">
          <button
            class="button is-link has-background-success"
            @click="addNewNote()"
            :disabled="!newNote"
          >
            Add Note
          </button>
        </div>
      </div>
    </div>

    <Note
      v-for="note in notes"
      :key="note.id"
      :note="note"
      @deleteNote="deleteThisNote"
    ></Note>
  </div>
</template>

<style scoped>

</style>