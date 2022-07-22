<template>
    <div class="tv-serie">
        Image: <img :src="basicImageUrl+poster_sizes[0]+tvSerie.poster_path" alt=""> <br></br>
        Titolo: {{tvSerie.name}} <br>
        Titolo Originale: {{tvSerie.original_name}} <br>
        <country-flag :country='tvSerie.original_language' size='normal'/> <br>
        <star-rating
        :increment="0.5"
        :max-rating="5"
        inactive-color="#999999"
        active-color="#F8D36B"
        :star-size="20"
        :read-only="true"
        :rating="tvSerie.vote_average/2"
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
    name: 'Serie',
    props: {
        tvSerie: {
            type: Object,
            required: true,
        },
    },
    components:{
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
.tv-serie{
    border: 1px solid black;
}
</style>