<template>
    <div class="list-of-movies">
        <Movie v-for="(movie,index) in movies" 
        :key="index"
        :movie="movie"
        />
    </div>
</template>

<script>
import Movie from './Movie.vue';
export default {
    props: {
        movies: {
            type: Array,
            required: true,
        },
    },
    components: {
        Movie,
    }

}
</script>

<style>
</style>