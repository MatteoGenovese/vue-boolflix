<template>
  <div id="app">
    <Header @search="searchFilm" />
    <Main :movies="cleanedMoviesList" />
  </div>
</template>

<script>
import Header from './components/Header.vue';
import Main from './components/Main.vue';
import axios from 'axios';

export default {
  name: 'App',
  components: {
    Header,
    Main,
  },
  methods: {
    searchFilm(needle) {
      axios.get(`https://api.themoviedb.org/3/search/movie?api_key=8b59d4e5705275542674ad47f794ccf6&query=${needle}`)
        .then((result) => {
          this.moviesFromApi = result.data.results;
          this.getMoviesList();
          this.printMoviesList();
        })
        .catch((error) => {
          console.warn(error);
        })
    },

    getMoviesList() {
      this.cleanedMoviesList = [];
      this.moviesFromApi.forEach(movie => {
        this.cleanedMoviesList.push({
          'title': movie.title,
          'original_title': movie.original_title,
          'original_language': movie.original_language,
          'vote_average': movie.vote_average
        });
      });
    },
    printMoviesList() {
      this.cleanedMoviesList.forEach(movie => {
        console.log(movie)
      });
    },
  },
  data: function () {
    return {
      moviesFromApi: [],
      cleanedMoviesList: [],
    }
  },
}
</script>

<style lang="scss">
</style>
