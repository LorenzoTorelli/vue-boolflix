<template>
  <div id="app">
    <Header/>
    <Main/>
  </div>
</template>

<script>
import Main from './components/Macro/Main.vue';
import Header from './components/Macro/Header.vue'

export default {
  name: 'App',
  components: {
    Main,
    Header
  }
}
</script>

<style lang="scss">
@import url("./assets/Variabili/Global.scss");


</style>
