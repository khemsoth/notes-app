<template>
  <div>
    <h3>{{ title }}</h3>
    <p>{{ desc }}</p>
  </div>
</template>

<script>
export default {
  name: 'Note',
  props: ['title', 'desc'],
  data() {
    return {

    }
  }
}
</script>

<style>

</style>