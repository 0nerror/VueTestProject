<template>
  <div id="app">
    <HelloWorld msg="Welcome to my Vue page!"/>
    <Warehouse></Warehouse>
  </div>
</template>

<script>
import Warehouse from './components/Warehouse.vue'
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'app',
  components: {
    Warehouse,
    HelloWorld
  }
}
</script>

<style>
  #app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
  }
  footer {
    clear: both;
    position: relative;
    height: 40px;
    margin-top: -40px;
    margin-left: 50%;
    font-size: .5em;
    padding: 1px;
    text-align: right;
  }
</style>