<template>
  <div id="app">
    <FixForm />
  </div>
</template>

<script>
//import HelloWorld from './components/HelloWorld.vue'
import FixForm from '@/components/FixForm'

export default {
  name: 'App',
  components: {
    //HelloWorld,
    FixForm
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
