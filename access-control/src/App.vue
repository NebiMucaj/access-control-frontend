<template>
  <div id="app">
  
    <AccessOverview/>
  </div>
</template>

<script>
import AccessOverview from './components/AccessOverview'
export default {
  name: 'App',
  components: {
    AccessOverview
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
