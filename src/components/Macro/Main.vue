<template>
  <div id="main" class="container">
   
    <!-- <p>{{risultato}}</p> -->
    <div v-if="data.searchBar != ''">
        <FilmContainer/>
        <SerieContainer/>
    </div>
    <div v-else>
        <h2>Cerca nella barra </h2>
    </div>

  </div>
</template>

<script>
import FilmContainer from "../sections/FilmContainer.vue"
import SerieContainer from "../sections/SerieContainer.vue"
import data from "../../share/data.js"

// import Serie from "../components/Main-components/Serie.vue"
export default {
    name: 'Main',
    components: {
        FilmContainer,
        SerieContainer
    },
    data() {
        return {
            data
        }
    }
    
}

</script>

<style lang="scss" scoped>

#main {
    padding-top:150px;
}
</style>