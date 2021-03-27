<template>
  <div>
    <form>
      <div class="create-note-input">
        <label for="title">Title: </label>
        <input class="create-input" type="text" v-model="title">
      </div>
      <div class="create-note-input">
        <label for="desc">Note: </label>
        <input class="create-input" type="text" v-model="desc">
      </div>
      <input class="btn add-note-btn" type="button" value="Add Note" v-on:click="addNote">
    </form>
  </div>
</template>

<script>
import { v4 as uuidv4 } from 'uuid'
export default {
  name: 'CreateNote',
  data() {
    return {
      id: null,
      title: '',
      desc: ''
    }
  },
  methods: {
    addNote(newNote) {
      newNote = {
        id: uuidv4(),
        title: this.title,
        desc: this.desc
      }
      this.$emit('add-note', newNote)
      this.id = null
      this.title = '',
      this.desc = ''
    }
  }
}
</script>

<style scoped>
  .create-note-input {
    margin: .5rem auto;
    width: 70vw;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    font-size: 1.3rem;
  }

  .add-note-btn {
    margin-top: 2rem;
  }

  @media (min-width: 320px) {
    .create-input {
      width: 50vw;
    }
  }

  @media (min-width: 600px) {
    .create-note-input {
      width: 60vw;
    }

  }

</style>