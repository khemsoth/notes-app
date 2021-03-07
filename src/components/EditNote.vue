<template>
  <div>
    <form>
      <div>
        <label for="title">Title: </label>
        <input type="text" v-model="title">
      </div>
      <div>
        <label for="desc">Note: </label>
        <input type="text" v-model="desc">
      </div>
      <input type="button" value="Update Note" v-on:click="updateNote">
    </form>
  </div>
</template>

<script>

export default {
  name: 'EditNote',
  props: ['oldNote'],
  data() {
    return {
      title: '',
      desc: ''
    }
  },
  watch: {
    oldNote: function(note) {
      this.title = note.noteTitle
      this.desc = note.noteDesc
    }
  },
  methods: {
    updateNote(updatedNote) {
      updatedNote = {
        updatedTitle: this.title,
        updatedDesc: this.desc
      }
      this.$emit('update-note', updatedNote)
    }
  }
}
</script>

<style>

</style>