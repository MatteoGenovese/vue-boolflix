<template>
  <main>
    <!-- <ListMovies :movies="movies" /> -->
  </main>
</template>

<script>
import ListMovies from './ListMovies.vue';

export default {
  name: 'Main',
  props: {
    ListMovies,
    movies: {
      type: Array,
      required: true,
    },

  }


}
</script>

<style>

</style>