<template>
    <div id="serie">
         <h4>{{ogg.name}}</h4>
        <h4>{{ogg.original_name}}</h4>
        <img v-if="ogg.original_language == 'it' " src="../../assets/flags/italy.png" alt="">
        <img v-else-if="ogg.original_language == 'en' " src="../../assets/flags/united-kingdom.png" alt="">
        <img v-else src="" alt="immagine non trovata">
        <h4>{{ogg.popularity}}</h4>
    </div>
</template>

<script>
export default {
    name:"Serie",
     props: {
        ogg: Object,
    },     
}
</script>

<style>

</style>