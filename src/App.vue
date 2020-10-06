<template>
  <div id="app">
    <img alt="Poke logo" src="./assets/logo.png">
    <PokeApi msg="Welcome to Your Pokemon App"/>
  </div>
</template>

<script>
import PokeApi from './components/PokeApi.vue'

export default {
  name: 'App',
  components: {
    PokeApi
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
