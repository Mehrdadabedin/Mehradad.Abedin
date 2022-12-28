<template>

 <PosFront msg="Snapsum"/>

  <div id="app" v-bind:style="{ position: 'absolute', top: '0' }">
    
  </div>
</template>

<script>
import PosFront from './components/PosFront.vue'
  



export default {
  name: 'App',
  components: {
   PosFront
    
  
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
