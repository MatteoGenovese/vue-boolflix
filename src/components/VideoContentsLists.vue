<template>
    <div>

            <h2>Movies</h2>
            <Movie v-for="movie in movies" :key="movie.id" :movie="movie" :tvSerie="tvSerie" />

            <h2>Tv Series</h2>
            <Serie v-for="tvSerie in tvSeries" :key="tvSerie.id" :tvSerie="tvSerie" />

    </div>

</template>

<script>
import Movie from './Movie.vue';
import Serie from './Serie.vue';

export default {
    name: 'VideoContentsLists',
    props: {
        movies: {
            type: Array,
            required: true,
        },
        tvSeries: {
            type: Array,
            required: true,
        },
    },
    components: {
        Movie,
        Serie,
    }
}
</script>

<style>
</style>