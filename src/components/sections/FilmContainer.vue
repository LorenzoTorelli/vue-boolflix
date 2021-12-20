<template>
  <section >
        <Film v-for="film in data.risultatoFilm" :key="film.id"
            :ogg = "film"
            />
    </section>
</template>

<script>
import data from "../../share/data.js"
import Film from "../commons/Film.vue"

export default {
    name:"FilmContainer",
        components: {
        Film,
    },
    data() {
        return {
            data
        }
    }
}
</script>


<style lang="scss" scoped>
</style>