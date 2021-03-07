<template>
  <div>
    <ul>
      <li is="Note" v-for="(note, index) in notes" 
      :key="note.id" 
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
          title: 'test',
          desc: 'another test'
        },
        {
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
      let i = this.notes.findIndex((obj => obj.title == u.updatedTitle))
      this.notes[i] = {
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