<script setup>
  import { computed } from "vue";

  const props = defineProps({
    note: {
      type: Object,
      required: true,

    }
  })

  const emit = defineEmits(['deleteNote'])

  const characterLength = computed(() => {
    const length = props.note.content.length;
    const description = `character${ length > 1 ? 's' : '' }`
    return `${length} ${description}`;
  })

  const deleteNoteHandler = () => {
    emit('deleteNote', props.note.id);
  }

</script>

<template>
  <div
    class="card mb-4"
  >
    <div class="card-content">
      <div class="content">
        {{ note.content }}
        <div class="has-text-right has-text-grey-light mt-2">
          <small>{{ characterLength }}</small>
        </div>
      </div>
    </div>
    <footer class="card-footer">
      <a href="#" class="card-footer-item">Edit</a>
      <a
        @click.prevent="deleteNoteHandler"
        href="#"
        class="card-footer-item"
      >
        Delete
      </a>
    </footer>
  </div>
</template>

<style scoped>

</style>