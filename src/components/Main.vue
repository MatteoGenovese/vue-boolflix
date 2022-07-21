<template>
  <main>
    <h1>film</h1>
    <MoviesList :movies="movies" />
    <br>
    <br>
    <br>
    <h1>serie tv</h1>

    <TvSeriesList :tvSeries="tvSeries" />
    

  </main>
</template>

<script>
import MoviesList from './MoviesList.vue';
import TvSeriesList from './TvSeriesList.vue';

export default {
  name: 'Main',
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
    MoviesList,
    TvSeriesList
  }


}
</script>

<style>

</style>