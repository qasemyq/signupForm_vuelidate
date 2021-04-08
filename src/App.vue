<template>
  <div id="app">
    <VuelidateForm/>
  </div>
</template>

<script>
import VuelidateForm from './components/VuelidateForm.vue'

export default {
  name: 'App',
  components: {
    VuelidateForm
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
