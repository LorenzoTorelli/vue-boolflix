<template>
    <section >
        <Film v-for="all in data.risultatoTrending" :key="all.id"
            :ogg = "all"
            />
    </section>
</template>

<script>
import data from "../../share/data.js"
import Film from "../commons/Film.vue"

export default {
    name:"TrndingContainer", 
    components: {
        Film
    },
    data() {
        return {
            data
        }
    },
    
}
</script>

<style lang="less" scoped>

</style>