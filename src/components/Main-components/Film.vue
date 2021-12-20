<template>
    <div id="film">
        <h4>{{ogg.title}}</h4>
        <h4>{{ogg.original_title}}</h4>
        <h4>{{ogg.original_language}}</h4>
        <h4>{{ogg.popularity}}</h4>
    </div>
</template>

<script>
export default {
    name:"Film",
    props: {
        ogg: Object,
    }
}
</script>

<style>

</style>