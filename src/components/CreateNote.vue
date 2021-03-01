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
export default {
  name: 'CreateNote',
  data() {
    return {
      title: '',
      desc: ''
    }
  },
  methods: {
    addNote(newNote) {
      newNote = {
        title: this.title,
        desc: this.desc
      }
      this.$emit('add-note', newNote)
      this.title = '',
      this.desc = ''
    }
  }
}
</script>

<style>

</style>