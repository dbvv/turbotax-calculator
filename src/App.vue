<template>
  <div id="app">
    <Calculator/>
    
  </div>
</template>

<script>

import Calculator from './components/Calculator.vue';

export default {
  name: 'App',
  components: {
    Calculator,
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto&display=swap');

#app {
  font-family:  Roboto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  margin-top: 60px;
  color: #393a3d;
}
</style>
