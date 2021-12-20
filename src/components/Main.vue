<template>
  <div id="main">
      <input type="text" v-model="searchBar">
      <button @click="search()">Cliccami</button>
      <!-- <p>{{risultato}}</p> -->
      <Film v-for="(film,index) in risultato" :key="index"
        :ogg = "film"
        />

  </div>
</template>

<script>
import axios from 'axios';
import Film from "../components/Main-components/Film.vue"
export default {
    name: 'Main',
    components: {
        Film,
    },
    data() {
        return {
            searchBar: '',
            risultato:[],
        }
    },
    methods: {
        search() {
            axios.get("https://api.themoviedb.org/3/search/movie/", {
                params: {
                    api_key:"609576eb1e4d09dcf2d6888012fbf56c",
                    query:this.searchBar
                }
            })
            .then(response => {
                this.risultato = response.data.results
                // console.log(response.data.results)
            })
            .catch(error => {
                console.log(error)
                this.errored = true
            })
        }
    }
}



</script>

<style>

</style>