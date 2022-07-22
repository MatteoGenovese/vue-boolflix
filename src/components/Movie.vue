<template>
    <div class="movie">
        Image: <img :src="basicImageUrl+poster_sizes[0]+movie.poster_path" alt="">
        Titolo: {{ movie.title }} <br>
        Titolo Originale: {{ movie.original_title }} <br>
        <country-flag :country='movie.original_language' size='normal' /> <br>
        Voto: {{ movie.vote_average }} <br>
        <br>
        <br>
    </div>

</template>

<script>
// https://www.npmjs.com/package/vue-country-flag
import CountryFlag from 'vue-country-flag';

export default {
    name: 'Movie',
    methods:{
        getImage(){

        }
    },
    props: {
        movie: {
            type: Object,
            required: true,
        },
    },
    components: {
        CountryFlag
    },
    data: function () {
        return {
            basicImageUrl: 'https://image.tmdb.org/t/p/',
            // https://www.themoviedb.org/talk/53c11d4ec3a3684cf4006400 available size of image
            poster_sizes: [
                "w92",
                "w154",
                "w185",
                "w342",
                "w500",
                "w780",
                "original"
            ]
        }
    },

}
</script>

<style>
.movie {
    border: 1px solid black;
}
</style>