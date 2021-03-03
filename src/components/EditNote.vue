<template>
  <div>
    <form>
      <div>
        <label for="title">Title: </label>
        <input type="text" v-model="oldTitle">
      </div>
      <div>
        <label for="desc">Note: </label>
        <input type="text" v-model="oldDesc">
      </div>
      <input type="button" value="Update Note" v-on:click="updateNote">
    </form>
  </div>
</template>

<script>

export default {
  name: 'EditNote',
  props: ['title', 'desc'],
  data() {
    return {
      oldTitle: '',
      oldDesc: ''
    }
  },
  methods: {
    updateNote(oldNote) {
      note = {
        oldTitle: this.oldTitle,
        oldDesc: this.oldDesc
      }
      this.$emit('edit-note', oldNote)
    }
  }
}
</script>

<style>

</style>