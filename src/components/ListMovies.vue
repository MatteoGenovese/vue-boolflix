<template>
    <div class="list-of-movies">
        <Movie />
    </div>
</template>

<script>
import Movie from './Movie.vue';
export default {
    props: {
        Movie,
        movies: {
            type: Array,
            required: true,
        },
    },

}
</script>

<style>
</style>