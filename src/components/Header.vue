<template>
  <header>
    <h1>{{ msg }}</h1>
  </header>
</template>

<script>
export default {
  name: 'Header',
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  header {
    background-color: #222;
    color: #fff;
    padding: 20px;
    margin: 0;
  }

  h1 {
    margin: 0;
  }
</style>
