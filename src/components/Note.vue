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
    }
  },
  methods: {
    editNote(note) {
      note = {
        title: this.title,
        desc: this.desc
      }
      console.log(note)
    },
    deleteNote() {
      this.$emit('delete-note')
    },
  }
}
</script>

<style>

</style>