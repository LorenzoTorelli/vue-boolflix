<template>
    <div id="header">
        <div id="titolo">
            <h2>BOOLFLIX</h2>
        </div>
        <div id="search-section">
            <input type="text" v-model="data.searchBar" placeholder="Cerca...." @keyup.enter="search()">
        </div>
    </div>
</template>

<script>
import axios from 'axios';
import data from "../../share/data.js"

export default {
    name:"Header",
   data() {
        return {
            data
        }
    },
    methods: {
        search() {
            const parametri= {
                 params: {
                    api_key:"609576eb1e4d09dcf2d6888012fbf56c",
                    query: data.searchBar,
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
    #header {
        height: 50px;
        width: 100%;
        display: flex;
        position: fixed;
        z-index: 1;
        background-color: black;
        
        #titolo, #search-section {
            align-self: center;
            padding: 0px 20px ;
            width: 50%;
        }
        #titolo {
            h2 {
                color:red;
                font-size: 30px;
            }
        }
        #search-section {
            display: flex;
            justify-content: end;
            input {
                background-color: black;
                border: 1px solid white;
                height: 25px;
                font-size: 15px;
                margin: 10px 10px;
                color: white;
                padding: 5px;
            }
           
        }

    }
</style>

