<template>
  <div id="app" class='calc-container'>

    <a href="#" @click.prevent="comp = 'home'">Title</a>
    <a href="#" @click.prevent="comp = 'Calc'">Calc</a>

    <template v-if="comp === 'Calc'">
      <transition mode="out-in" name="animate__animated calc-transition" enter-active-class="animate__animated animate__bounce" leave-active-class="animate__animated animate__flipOutX" appear="true">

        <div>
           <Calc></Calc>
        </div>

      </transition>

    </template>

    <template v-else>
      <transition mode="out-in" name="animate__animated calc-transition" enter-active-class="animate__animated animate__bounce" leave-active-class="animate__animated animate__flipOutX" appear="true">
        <h1>Kalkulator</h1>
      </transition>
    </template>

  </div>
</template>

<script>


import Calc from './components/Calc'

export default {
  name: 'App',
  components: {
    Calc
  },
  data() {
    return {
      comp:'Calc'
    }
  },
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
