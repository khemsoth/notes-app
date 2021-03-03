<template>
  <div id="app">
    <CreateNote v-on:add-note="addNote"/>
    <NoteList :newNote="newNote" v-on:edit-note="editNote" />
    <EditNote :class="{ active: isActive }"/>

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
      isActive: false
    }
  },
  methods: {
    addNote(newNote) {
      this.newNote = newNote
    },
    editNote(oldNote) {
      this.isActive = !this.isActive
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
