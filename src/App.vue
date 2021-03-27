<template>
  <div id="app">
    <Header :class="{ unfocus: isActive }"/>
    <main class="main" :class="{ unfocus: isActive }">
      <CreateNote v-on:add-note="addNote"/>
      <NoteList :newNote="newNote" :updatedNote="updatedNote" v-on:edit-note="editNote" />
    </main>
    <div :class="{ modalCont: isActive }">
      <EditNote class="edit-note" :oldNote="oldNote" :class="{ active: isActive }" v-on:update-note="updateNote" v-on:cancel-update="cancelUpdate" />
    </div>
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
  watch: {
    isActive() {
      document.body.style.overflow = this.isActive ? 'hidden' : ''
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
      this.isActive = true
      this.oldNote = oldNote
    },
    updateNote(updatedNote) {
      this.updatedNote = updatedNote
      this.isActive = false
    },
    cancelUpdate() {
      this.isActive = false
    }
  },  
}
</script>

<style>

  body {
    background-color: #98d2eb;
    margin: 0;
    height: 100vh;
    color: #49392c;
    overflow-x: hidden;
  }

  main {
    margin-top: 4rem;
  }

  .unfocus {
    opacity: .5;
    overflow: hidden;
    pointer-events: none;
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

  .edit-note {
    display: none;
    z-index: 5;
    justify-content: center;
    background-color: rgba(255, 255, 255,  .9);
    width: 80vw;
  }

  .active {
    display: block;
    position: fixed;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    overflow: hidden;
    
  }

  .modal-cont {
    height: 100vh;
    overflow-y: hidden;
  }

  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    display: flex;
    flex-direction: column;
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
