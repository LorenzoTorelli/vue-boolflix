<template>
  <div id="main" class="container">
    <input type="text" v-model="searchBar">
    <button @click="search()">Cliccami</button>
    <!-- <p>{{risultato}}</p> -->
    <FilmContainer/>
    <SerieContainer/>

  </div>
</template>

<script>
import axios from 'axios';
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
            searchBar: '',
            data
        }
    },
    methods: {
        search() {
            const parametri= {
                 params: {
                    api_key:"609576eb1e4d09dcf2d6888012fbf56c",
                    query: this.searchBar,
                    language:'it-IT'
                 }
            }
            axios.get("https://api.themoviedb.org/3/search/movie/", parametri)
            .then(response => {
                data.risultatoFilm= response.data.results
            });

            axios.get("https://api.themoviedb.org/3/search/tv/", parametri)
            .then(response => {
                data.risultatoSerie= response.data.results
            })
        },
    }
}

</script>

<style lang="scss" scoped>


</style>