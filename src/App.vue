<template>
  <div id="app">
    <Header msg="Welcome to Chris's Palindrome Checker"/>
    <Checker />
  </div>
</template>

<script>
import Header from './components/Header.vue';
import Checker from './components/Checker.vue';

export default {
  name: 'app',
  components: {
    Header,
    Checker
  }
}
</script>

<style>
html, body {
  margin: 0;
  padding: 0;
  height: 100%;
  background-color: lightblue;
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
