<template>
  <div id="app">
    <Header />    
    <router-view />
  </div>
</template>

<script>
import Header from './components/Header.vue'

export default {
  name: "App",
  components: {
    Header
  }
}
</script>


<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  line-height: 1.4;
}
</style>
