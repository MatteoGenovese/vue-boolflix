<template>
    <div class="movie">
        Titolo: {{movie.title}} <br>
        Titolo Originale: {{movie.original_title}} <br>
        <country-flag :country='movie.original_language' size='normal'/> <br>
        Voto: {{movie.vote_average}} <br>
        <br>
        <br>
    </div>

</template>

<script>
// https://www.npmjs.com/package/vue-country-flag
import CountryFlag from 'vue-country-flag';

export default {
    name: 'Movie',

    props: {
        movie: {
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
.movie{
    border: 1px solid black;
}
</style>