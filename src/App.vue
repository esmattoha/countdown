<template>
  <div id="app">
      <h1>Time Count Down</h1>
      <Timer />
  </div>
</template>

<script>
import Timer from './components/timer'

export default {
  name: 'App',
  components:{
    Timer
  }
  
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}

</style>
