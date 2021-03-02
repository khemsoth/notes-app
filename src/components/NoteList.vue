<template>
  <div>
    <ul>
      <li is="Note" v-for="(note, index) in notes" :key="note.id" :title="note.title" :desc="note.desc" v-on:delete-note="deleteNote(index)">
      </li>
    </ul>
  </div>
</template>

<script>
import Note from './Note'
export default {
  name: 'NoteList',
  props: {
    newNote: Object
  },
  components: {
    Note
  },
  data() {
    return {
      notes: [
        {
          title: 'test',
          desc: 'another test'
        },
        {
          title: 'test2',
          desc: 'another test 2'
        }
      ]
    }
  },
  watch: {
    newNote(n) {
      this.notes.push(n)
    }
  },
  methods: {
    deleteNote(index) {
      this.notes.splice(index, 1)
    }
  }
}
</script>

<style>

</style>