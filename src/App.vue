<template>
  <div id="app" class='calc-container'>
    <Calc></Calc>
  </div>
</template>

<script>


import Calc from './components/Calc'

export default {
  name: 'App',
  components: {
    Calc
  }
}
</script>

<style>
#app {
  padding-left: 10vw;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
