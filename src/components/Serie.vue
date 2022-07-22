<template>
    <div class="tv-serie">
        Titolo: {{tvSerie.name}} <br>
        Titolo Originale: {{tvSerie.original_name}} <br>
        <country-flag :country='tvSerie.original_language' size='normal'/> <br>
        Voto: {{tvSerie.vote_average}} <br>
        <br>
        <br>
    </div>



</template>

<script>
// https://www.npmjs.com/package/vue-country-flag
import CountryFlag from 'vue-country-flag';

export default {
    name: 'Serie',
    props: {
        tvSerie: {
            type: Object,
            required: true,
        },
    },
    components:{
        CountryFlag
    }

}
</script>

<style>
.tv-serie{
    border: 1px solid black;
}
</style>