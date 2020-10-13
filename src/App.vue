<template>
  <div id="app">
    <formT/>
  </div>
</template>

<script>
import formT from './components/formT.vue'

export default {
  name: 'App',
  components: {
    formT,
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
