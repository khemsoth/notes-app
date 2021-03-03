<template>
  <div>
    <h3>{{ title }}</h3>
    <p>{{ desc }}</p>
    <input type="button" value="Edit" v-on:click="editNote">
    <input type="button" value="Delete" v-on:click="deleteNote">
  </div>
</template>

<script>
export default {
  name: 'Note',
  props: ['title', 'desc'],
  data() {
    return {
      oldTitle: '',
      oldDesc: ''
    }
  },
  methods: {
    editNote(oldNote) {
      this.oldTitle = this.title
      this.oldDesc = this.desc
      oldNote = {
        oldTitle: this.oldTitle,
        oldDesc: this.oldDesc
      }
      this.$emit('edit-note', oldNote)
    },
    deleteNote() {
      this.$emit('delete-note')
    },
  }
}
</script>

<style>

</style>