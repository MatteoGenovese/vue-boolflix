<template>
  <main>
    <MoviesList :movies="movies" />

  </main>
</template>

<script>
import MoviesList from './MoviesList.vue';

export default {
  name: 'Main',
  props: {
    movies: {
      type: Array,
      required: true,
    },
  },
  components: {
    MoviesList,
  }


}
</script>

<style>

</style>