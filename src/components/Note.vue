<template>
  <div class="note">
    <h3>{{ title }}</h3>
    <p>{{ desc }}</p>
    <div class="btn-cont">
      <input class="btn note-btn" type="button" value="Edit" v-on:click="editNote">
      <input class="btn note-btn" type="button" value="Delete" v-on:click="deleteNote">
    </div>
  </div>
</template>

<script>
export default {
  name: 'Note',
  props: {
    title: String,
    desc: String,
    id: String
  },
  data() {
    return {
      oldID: null,
      oldTitle: '',
      oldDesc: '',
    }
  },
  methods: {
    editNote(oldNote) {
      this.oldID = this.id
      this.oldTitle = this.title
      this.oldDesc = this.desc
      oldNote = {
        oldID: this.oldID,
        oldTitle: this.oldTitle,
        oldDesc: this.oldDesc
      }
      this.$emit('edit-note', oldNote)
     let x = JSON.parse(localStorage.getItem('notes'))
     let i = x.findIndex(el => console.log(el.id))
     
    },
    deleteNote() {
      this.$emit('delete-note')
    },
  }
}
</script>

<style scoped>
  .note {
    width: 80%;
    margin: 2rem auto;
    background-color: rgba(255, 255, 255, .8);
    padding: .5rem;
    border-radius: 1rem;
  }

  .note-btn {
    width: 40%;
    height: 2rem;
    padding: 0;
  }

  .btn-cont {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
  }

</style>