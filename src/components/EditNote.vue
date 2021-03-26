<template>
  <div>
    <h1>Edit Note</h1>
    <form>
      <div class="edit-note-field">
        <label for="title">Title: </label>
        <input type="text" v-model="title">
      </div>
      <div class="edit-note-field">
        <label for="desc">Note: </label>
        <input type="text" v-model="desc">
      </div>
      <input class="btn update-btn" type="button" value="Update Note" v-on:click="updateNote">
      <input class="btn update-btn" type="button" value="Cancel" v-on:click="cancelUpdate">

    </form>
  </div>
</template>

<script>

export default {
  name: 'EditNote',
  props: ['oldNote'],
  data() {
    return {
      id: null,
      title: '',
      desc: ''
    }
  },
  watch: {
    oldNote: function(note) {
      this.id = note.noteID
      this.title = note.noteTitle
      this.desc = note.noteDesc
    }
  },
  methods: {
    updateNote(updatedNote) {
      updatedNote = {
        id: this.id,
        updatedTitle: this.title,
        updatedDesc: this.desc
      }
      this.$emit('update-note', updatedNote)
      this.id = null,
      this.title = '', 
      this.desc = ''
    },
    cancelUpdate() {
      this.$emit('cancel-update')
    }
  }
}
</script>

<style scoped>
  .edit-note-field {
    margin: 1rem 0;
  }

  .update-btn {
    margin: 1rem;
  }

</style>