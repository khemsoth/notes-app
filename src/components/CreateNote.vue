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
      <input type="button" value="Add Note" v-on:click="addNote">
    </form>
  </div>
</template>

<script>
import { v4 as uuidv4 } from 'uuid'
export default {
  name: 'CreateNote',
  data() {
    return {
      id: null,
      title: '',
      desc: ''
    }
  },
  methods: {
    addNote(newNote) {
      newNote = {
        id: uuidv4(),
        title: this.title,
        desc: this.desc
      }
      this.$emit('add-note', newNote)
      this.id = null
      this.title = '',
      this.desc = ''
    }
  }
}
</script>

<style>

</style>