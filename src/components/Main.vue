<template>
  <div id="main">
    <input type="text" v-model="searchBar">
    <button @click="searchTV(),searchFilm()">Cliccami</button>
    <!-- <p>{{risultato}}</p> -->
    <Film v-for="(film,index) in risultatoFilm" :key="index"
        :ogg = "film"
        />
    <Serie v-for="(serie,index) in risultatoTv" :key="index"
        :ogg = "serie"
    />
  </div>
</template>

<script>
import axios from 'axios';
import Film from "../components/Main-components/Film.vue"
import Serie from "../components/Main-components/Serie.vue"
export default {
    name: 'Main',
    components: {
        Film,
        Serie
    },
    data() {
        return {
            searchBar: '',
            risultatoFilm:[],
            risultatoTv: [],

        }
    },
    methods: {
        searchFilm() {
            axios.get("https://api.themoviedb.org/3/search/movie/", {
                params: {
                    api_key:"609576eb1e4d09dcf2d6888012fbf56c",
                    query: this.searchBar
                }
            })
            .then(response => {
                this.risultatoFilm= response.data.results
                // console.log(response.data.results)
            })
            .catch(error => {
                console.log(error)
                this.errored = true
            })

        },
        searchTV() {
            axios.get("https://api.themoviedb.org/3/search/tv/", {
                params: {
                    api_key:"609576eb1e4d09dcf2d6888012fbf56c",
                    query: this.searchBar
                }
            })
            .then(response => {
                this.risultatoTv= response.data.results
                // console.log(response.data.results)
            })
            .catch(error => {
                console.log(error)
                this.errored = true
            })

        },

    }
}



</script>

<style>

</style>