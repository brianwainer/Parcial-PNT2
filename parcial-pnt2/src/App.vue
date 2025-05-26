<template>
  <div id="app">
    <h1>Parcial PNT2</h1>
    <ParcialTransformer />
  </div>
</template>

<script>
import ParcialTransformer from './components/Parcial.vue'

export default {
  name: 'App',
  components: {
    ParcialTransformer
  }
}
</script>

<style>
#app {
  font-family: Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
