<template>
    <div id="film" class="card">
        <img v-if="ogg.poster_path != null" :src="'https://image.tmdb.org/t/p/' + 'w154' + ogg.poster_path" alt="">
        <img class= "poster-vuoto" v-else src="https://img.myloview.it/poster/oggetto-vuoto-lembo-film-isolato-400-31409275.jpg" alt="">
        <div class="card-title">
            <h4>{{ogg.title}}</h4>
            <h4>{{ogg.original_title}}</h4>
        </div>
        <div class="flag">
            <img v-if="ogg.original_language == 'it' " src="../../assets/flags/italy.png" alt="">
            <img v-else-if="ogg.original_language == 'en' " src="../../assets/flags/united-kingdom.png" alt="">
            <img v-else src="" alt="immagine non trovata">
        </div>
        <h4>{{ogg.popularity}}</h4>
    </div>
</template>

<script>
export default {
    name:"Film",
    props: {
        ogg: Object,
    },          
    
}
</script>

<style lang="scss" scoped>

@import url("../../assets/Variabili/Global.scss");

</style>