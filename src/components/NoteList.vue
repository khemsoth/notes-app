<template>
  <div>
    <ul class="note-list">
      <li
      is="Note" 
      v-for="(note, index) in notes" 
      :key="note.id" 
      :id="note.id"
      :title="note.title"
      :desc="note.desc"
      v-on:delete-note="deleteNote(index)"
      v-on:edit-note="editNote"
      >
      </li>
    </ul>
    <input class="btn clear-btn" type="button" value="Clear all" v-on:click="clearAll">
  </div>
</template>

<script>
import Note from './Note'
import EditNote from './EditNote'

export default {
  name: 'NoteList',
  props: {
    newNote: Object,
    updatedNote: Object,
  },
  components: {
    Note,
    EditNote
  },
  data() {
    return {
      oldNote: {},
      notes: [],
      editVisible: false
    }
  },
  created() {
    let noteCheck = JSON.parse(localStorage.getItem('notes'))
    if(!noteCheck) {
      let noteList = []
      localStorage.setItem('notes', JSON.stringify(noteList))
    } else {
      let noteList = JSON.parse(localStorage.getItem('notes'))
      for(var i = 0; i < noteList.length; i++) {
        this.notes.push(noteList[i])
      }
    }
  },
  watch: {
    newNote(n) {
      this.notes.push(n)
    },
    updatedNote(u) {
      let i = this.notes.findIndex((obj => obj.id == u.id))
      this.notes[i] = {
        id: u.id,
        title: u.updatedTitle,
        desc: u.updatedDesc
      }
      this.$forceUpdate()
      let newList = this.notes
      localStorage.setItem('notes', JSON.stringify(newList))
    }
  },
  methods: {
    deleteNote(index) {
      this.notes.splice(index, 1)
      let newList = this.notes
      localStorage.setItem('notes', JSON.stringify(newList))
    },
    editNote(oldNote) {
      this.oldNote = {
        noteID: oldNote.oldID,
        noteTitle: oldNote.oldTitle,
        noteDesc: oldNote.oldDesc
      }
      this.editVisible = !this.editVisible
      this.$emit('edit-note', this.oldNote)
    },
    clearAll() {
      
      localStorage.clear()
      this.notes = []
      /*
     let x = JSON.parse(localStorage.getItem('notes'))
     let i = x.findIndex(el => el.id = "60317d21-9d2b-4892-95b5-f5e0baf9e2f5")
     console.log(i)
     */
    }
  }
}
</script>

<style scoped>
  .note-list {
    padding: 0;
  }

  .clear-btn {
    margin: 5rem 0;
  }
</style>