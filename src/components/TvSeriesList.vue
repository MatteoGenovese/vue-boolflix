<template>
    <div class="list-of-tv-series">
        <TvSerie v-for="(tvSerie,index) in tvSeries" 
        :key="index"
        :tvSerie="tvSerie"
        />
    </div>
</template>

<script>
import TvSerie from './TvSerie.vue';

export default {
    name: 'TvSeriesList',
    props: {
        tvSeries: {
            type: Array,
            required: true,
        },
    },
    components: {
        TvSerie,
    }
}
</script>

<style>
</style>