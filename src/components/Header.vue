<template>
  <div class="header">
    <h1 class="header-title">Jot It Down</h1>
    <p>Fill in the fields below to leave a note</p>
  </div>
</template>

<script>
export default {
  name: 'Header'

}
</script>

<style>
  .header {
    background-color: #e1f2fe;
    width: 100vw;
    height: 30vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    font-size: 1.5rem;
  }

  .header-title {
    margin: 0 auto;
  }
</style>