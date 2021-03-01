<template>
  <div id="app">
    <CreateNote v-on:add-note="addNote"/>
    <NoteList :newNote="newNote"/>
  </div>
</template>

<script>
import NoteList from './components/NoteList'
import CreateNote from './components/CreateNote'

export default {
  name: 'App',
  components: {
    NoteList,
    CreateNote
  },
  data() {
    return {
      newNote: {}
    }
  },
  methods: {
    addNote(newNote) {
      this.newNote = newNote
    }
  },  
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
