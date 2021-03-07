<template>
  <div>
    <ul>
      <li is="Note" v-for="(note, index) in notes" 
      :key="note.id" 
      :id="note.id"
      :title="note.title"
      :desc="note.desc"
      v-on:delete-note="deleteNote(index)"
      v-on:edit-note="editNote"
      >
      </li>
    </ul>
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
      notes: [
        {
          id: '1',
          title: 'test',
          desc: 'another test'
        },
        {
          id: '2',
          title: 'test2',
          desc: 'another test 2'
        }
      ],
      editVisible: false
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
    }
  },
  methods: {
    deleteNote(index) {
      this.notes.splice(index, 1)
    },
    editNote(oldNote) {
      this.oldNote = {
        noteID: oldNote.oldID,
        noteTitle: oldNote.oldTitle,
        noteDesc: oldNote.oldDesc
      }
      this.editVisible = !this.editVisible
      this.$emit('edit-note', this.oldNote)
    }
  }
}
</script>

<style>

</style>