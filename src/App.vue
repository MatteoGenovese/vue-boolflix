<template>
  <div id="app">
    <Header @search="searchFilmAndTvSeries" />
    <Main :movies="cleanedMoviesList" :tvSeries="cleanedTvSeriesList" />
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
    searchFilmAndTvSeries(needle) {
      axios.get(`https://api.themoviedb.org/3/search/movie?api_key=8b59d4e5705275542674ad47f794ccf6&query=${needle}`)
        .then((result) => {
          this.moviesFromApi = result.data.results;
          this.getMoviesList();
          this.printMoviesList();
        })
        .catch((error) => {
          console.warn(error);
        })

      axios.get(`https://api.themoviedb.org/3/search/tv?api_key=8b59d4e5705275542674ad47f794ccf6&query=${needle}`)
        .then((result) => {
          this.tvSeriesFromApi = result.data.results;
          this.getTvSeriesList();
          this.printTvSeriesList();
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
      this.cleanedTvSeriesList.forEach(movie => {
        console.log(movie)
      });
    },
    getTvSeriesList() {
      this.cleanedTvSeriesList = [];
      this.tvSeriesFromApi.forEach(tvSerie => {
        this.cleanedTvSeriesList.push({
          'name': tvSerie.name,
          'original_name': tvSerie.original_name,
          'original_language': tvSerie.original_language,
          'vote_average': tvSerie.vote_average
        });
      });
    },
    printTvSeriesList() {
      this.cleanedTvSeriesList.forEach(tvSerie => {
        console.log(tvSerie)
      });
    },
  },
  data: function () {
    return {
      moviesFromApi: [],
      cleanedMoviesList: [],

      tvSeriesFromApi: [],
      cleanedTvSeriesList: [],
    }
  },
}
</script>

<style lang="scss">
</style>
