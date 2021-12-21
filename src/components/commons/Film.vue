<template>
    <div id="film" class="card" @mouseover="active = false" @mouseout="active = true">

        <!-- Immagine poster  -->
        <div class="film-poster" v-show="active" >
            <img class="poster" v-if="ogg.poster_path != null" :src="'https://image.tmdb.org/t/p/' + 'w342' + ogg.poster_path" alt="">
            <img class= "poster-vuoto" v-else :src="require('../../assets/img/poster.jpeg')" alt="">
        </div>

        <!-- Informazioni Film  -->
        <div class="film-info" v-show="!active">
            <div class="card-title card-sec">
                <h3 v-if="ogg.title != undefined"><strong>Titolo: </strong>{{ogg.title}}</h3>
                <h3 v-else><strong>Titolo: </strong>{{ogg.name}}</h3>
                <h3 v-if="ogg.original_title != undefined"><strong>Titolo originale: </strong>{{ogg.original_title}}</h3>
                <h3 v-else><strong>Titolo originale: </strong>{{ogg.original_name}}</h3>
            </div>
            <div class="flag card-sec">
                <img v-if="img!=null" :src="img" alt="">
                <span v-else>{{ogg.original_language}}</span>
            </div>
            <div class="card-sec">
                Voto: 
                <span v-for="(star, index) in 5" :key="index">
                    <span class="stellaPiena" v-if="index < stelle">&#9733;</span>
                    <span class="stellaVuota" v-else>&#9734;</span>
                </span>
            </div>
            <div class="card-sec overview">
                <strong>Overview: </strong>
                <div class="paragrafo">
                    <p>{{ogg.overview}}</p>
                </div>
            </div>
        </div>

    </div>
</template>

<script>
export default {
    name:"Film",
    props: {
        ogg: Object,
    },          

    data() {
        return {
            stelle: this.stars(this.ogg.vote_average),
            active:'true'
        }
    },
    computed: {
        img() {
            let image = ''
            try {
                 image = require('../../assets/flags/' + this.ogg.original_language + '.png');
            }
            catch {
                image = null;
            }
            return image;
        }
    },

    methods: {
        stars: function(n) { 
           return Math.round(n/2)
        },
    }
    
}
</script>

<style lang="scss" scoped>
    .film-poster {
       height: 100%;
       overflow: hidden; 
       .poster {
           height: 100%;
       } 
       .poster-vuoto {
           width: 342px;
       }
    }

    .film-info {
        padding: 40px 20px;
        .card-sec{
            margin:10px 0px;
            height: 20%;
        }
        strong {
            font-size: 20px;
        }
        h3 {
            font-size: 15px;
        }
        .stellaPiena, .stellaVuota {
            color: yellow;
        }

        .overview { 
            height: 40%;
            
            .paragrafo {
                height: 250px;
                overflow: hidden;
                text-overflow: ellipsis;
                white-space: normal;
            }

        }
    }

</style>