<template>
  <section>
        <Film v-for="serie in data.risultatoSerie" :key="serie.id"
            :ogg = "serie"
            />
    </section>
</template>

<script>
import data from "../../share/data.js"
import Film from "../commons/Film.vue"
export default {
    name:"SerieContainer",
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
@import url("../../assets/Variabili/Global.scss");
</style>

