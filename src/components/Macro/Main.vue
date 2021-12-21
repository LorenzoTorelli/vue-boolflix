<template>
  <div id="main" class="container">
   
    <!-- <p>{{risultato}}</p> -->
    <FilmContainer/>
    <SerieContainer/>

  </div>
</template>

<script>
import FilmContainer from "../sections/FilmContainer.vue"
import SerieContainer from "../sections/SerieContainer.vue"

// import Serie from "../components/Main-components/Serie.vue"
export default {
    name: 'Main',
    components: {
        FilmContainer,
        SerieContainer
    },
    
}

</script>

<style lang="scss" scoped>

#main {
    padding-top:150px;
}
</style>