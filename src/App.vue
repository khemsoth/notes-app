<template>
  <div id="app">
    <CreateNote v-on:add-note="addNote"/>
    <NoteList :newNote="newNote" :updatedNote="updatedNote" v-on:edit-note="editNote" />
    <EditNote :oldNote="oldNote" :class="{ active: isActive }" v-on:update-note="updateNote" />

  </div>
</template>

<script>
import NoteList from './components/NoteList'
import CreateNote from './components/CreateNote'
import EditNote from './components/EditNote'

export default {
  name: 'App',
  components: {
    NoteList,
    CreateNote,
    EditNote
  },
  data() {
    return {
      newNote: {},
      oldNote: {},
      updatedNote: {},
      isActive: false
    }
  },
  methods: {
    addNote(newNote) {
      this.newNote = newNote
    },
    editNote(oldNote) {
      this.isActive = !this.isActive
      this.oldNote = oldNote
    },
    updateNote(updatedNote) {
      this.updatedNote = updatedNote
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

.active {
  background-color: red;
}

</style>
