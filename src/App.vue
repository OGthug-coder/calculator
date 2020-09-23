<template>
  <Calculator />
</template>

<script>
import Calculator from './components/Calculator.vue'

export default {
  name: 'App',
  components: {
    Calculator
  }
}
</script>

<style>

#app {
  min-height: 100vh;
  min-width: 100vw;
  background-color: #000000;
}

</style>
