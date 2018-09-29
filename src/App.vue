<template>
  <div id="app">
    <Consume/>
  </div>
</template>

<script>
import Consume from './components/Consume.vue'

export default {
  name: 'app',
  components: {
    Consume
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
