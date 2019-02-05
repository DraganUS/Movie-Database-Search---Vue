<template>
  <div id="app">
    
    <movieSearch />
  </div>
</template>

<script>
import movieSearch from './components/movieSearch.vue'

export default {
  name: 'app',
  components: {
    movieSearch
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
  
}
</style>
