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
  props: {
    title: String,
    desc: String,
    id: String
  },
  data() {
    return {
      oldID: null,
      oldTitle: '',
      oldDesc: '',
    }
  },
  methods: {
    editNote(oldNote) {
      this.oldID = this.id
      this.oldTitle = this.title
      this.oldDesc = this.desc
      oldNote = {
        oldID: this.oldID,
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