<template>
    <div class="movie">
        Image: <img :src="basicImageUrl + poster_sizes[0] + movie.poster_path" alt=""> <br>
        Titolo: {{ movie.title }} <br>
        Titolo Originale: {{ movie.original_title }} <br>
        <country-flag :country='movie.original_language' size='normal' /> <br>
        <star-rating
        :increment="0.5"
        :max-rating="5"
        inactive-color="#999999"
        active-color="#F8D36B"
        :star-size="20"
        :read-only="true"
        :rating="movie.vote_average/2"
        >
        </star-rating>
        <br>
        <br>
    </div>

</template>

<script>
// https://www.npmjs.com/package/vue-country-flag country flag documentation
import CountryFlag from 'vue-country-flag';
// https://www.npmjs.com/package/vue-star-rating star rating documentation
import StarRating from 'vue-star-rating'

export default {
    name: 'Movie',
    props: {
        movie: {
            type: Object,
            required: true,
        },
    },
    components: {
        CountryFlag,
        StarRating
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