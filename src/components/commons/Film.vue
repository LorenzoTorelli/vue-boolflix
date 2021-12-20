<template>
    <div id="film" class="card">
        <img v-if="ogg.poster_path != null" :src="'https://image.tmdb.org/t/p/' + 'w154' + ogg.poster_path" alt="">
        <img class= "poster-vuoto" v-else src="https://img.myloview.it/poster/oggetto-vuoto-lembo-film-isolato-400-31409275.jpg" alt="">
        <div class="card-title">
            <h4 v-if="ogg.title != undefined">{{ogg.title}}</h4>
            <h4 v-else>{{ogg.name}}</h4>
            <h4 v-if="ogg.original_title != undefined">{{ogg.original_title}}</h4>
            <h4 v-else>{{ogg.original_name}}</h4>
        </div>

        <div class="flag">
            <img v-if="img!=null" :src="img" alt="">
            <span v-else>{{ogg.original_language}}</span>
        </div>

        <div>
            <span v-for="(star, index) in 5" :key="index">
                <span v-if="index < stelle">&#9733;</span>
                <span v-else>&#9734;</span>
            </span>
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


</style>