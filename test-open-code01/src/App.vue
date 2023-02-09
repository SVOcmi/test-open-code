<template>
  <div id="app">
    <div class="conteiner-text">
      <div class="text-name">Название</div>
    </div>
    <div id="el1"></div>
    <div id="el2"></div>
    <div id="el3"></div>
    <div id="el4"></div>
    <canvas id="canvas"></canvas>
  </div>
</template>

<script>
import zone from './components/zone.vue'
import './components/zone.css'

export default {
  name: 'app',
  components: {
    mounted: {
      zone
    }
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
  
}
</style>
