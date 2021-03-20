<template>
  <div id="app">
    <Header />
    <main class="main">
      <CreateNote v-on:add-note="addNote"/>
      <NoteList :newNote="newNote" :updatedNote="updatedNote" v-on:edit-note="editNote" />
      <!--<EditNote :oldNote="oldNote" :class="{ active: isActive }" v-on:update-note="updateNote" />-->
    </main>
  </div>
</template>

<script>
import NoteList from './components/NoteList'
import CreateNote from './components/CreateNote'
import EditNote from './components/EditNote'
import Header from './components/Header'

export default {
  name: 'App',
  components: {
    NoteList,
    CreateNote,
    EditNote,
    Header
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
      let note = {
        id: newNote.id,
        title: newNote.title,
        desc: newNote.desc
      }
      let noteList = JSON.parse(localStorage.getItem('notes'))
      noteList.push(note)
      localStorage.setItem('notes', JSON.stringify(noteList))
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
  body {
    background-color: #98d2eb;
    margin: 0;
    height: 100vh;
  }

  main {
    margin-top: 4rem;
  }

  .btn {
    background-color: #77625c;
    color: #ffffff; 
    border-color: #77625c;
    border-radius: .5rem;
    padding: 1rem;
    width: 10rem;
  }

  .btn:hover {
    background-color: #e1f2fe;
    border-color: #77625c;
    color: #77625c;
    cursor: pointer;
  }

  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
  }

  @media (min-width: 320px) {

  }

  @media (min-width: 480px) {
    
  }

  @media (min-width: 600px) {
    
  }

  @media (min-width: 801px) {
    
  }

 @media (min-width: 1025px) {
    
  }

 @media (min-width: 1281px) {
    
  }

</style>
