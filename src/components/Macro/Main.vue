<template>
  <div id="main" class="container">
   
    <!-- <p>{{risultato}}</p> -->
    <div v-if="data.searchBar != '' && data.clean == 'false'">
        <h2>Films</h2>
        <FilmContainer/>

        <h2>Tv Shows</h2>
        <SerieContainer/>
    </div>
    <div v-els >
        <h2>Top shows of the week:</h2>
        <TrendingContainer/>
    </div>

  </div>
</template>

<script>
import axios from 'axios';
import FilmContainer from "../sections/FilmContainer.vue"
import SerieContainer from "../sections/SerieContainer.vue"
import TrendingContainer from "../sections/TrendingContainer.vue"
import data from "../../share/data.js"

export default {
    name: 'Main',
    components: {
        FilmContainer,
        SerieContainer,
        TrendingContainer,
    },
    data() {
        return {
            data
        }
    },
    created() {
            const parametri= {
                 params: {
                    api_key:"609576eb1e4d09dcf2d6888012fbf56c",
                    language:'it-IT'

                 }
            }
            axios.get("https://api.themoviedb.org/3/trending/all/week?", parametri)
            .then(response => {
                data.risultatoTrending = response.data.results
            });
        }
    
    
}

</script>

<style lang="scss" scoped>

#main {
    padding-top:150px;
    h2 {
        margin-bottom: 50px;
        text-transform: uppercase;
        font-size: 30px;
    }
}
</style>