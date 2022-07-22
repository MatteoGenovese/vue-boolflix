<template>
    <div>

        <h2>Movies</h2>
        <div class="list-of-movies">
            <Movie v-for="movie in movies" :key="movie.id" :movie="movie" />
        </div>
        <h2>Tv Series</h2>
        <div class="list-of-series">
            <Serie v-for="tvSerie in tvSeries" :key="tvSerie.id" :tvSerie="tvSerie" />
        </div>

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

<style lang="scss" >
.list-of-movies,
.list-of-series{
    display : flex;
    flex-wrap: wrap;
    justify-content: space-between;
    row-gap: 20px;
}

</style>