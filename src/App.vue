<template>
  <div id="app">
    <Header @search="searchFilmAndTvSeries" />
    <Main :movies="moviesFromApi" :tvSeries="tvSeriesFromApi" />
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
      axios.get(`${this.apiMoviesUrl}?api_key=${this.apiKey}&query=${needle}`)
        .then((result) => {
          this.moviesFromApi = result.data.results;
          
        })
        .catch((error) => {
          console.warn(error);
        })

      axios.get(`${this.apiTvsUrl}?api_key=${this.apiKey}&query=${needle}`)
        .then((result) => {
          this.tvSeriesFromApi = result.data.results;
        })
        .catch((error) => {
          console.warn(error);
        })
    },
  },
  data: function () {
    return {

      apiKey: '8b59d4e5705275542674ad47f794ccf6',
      apiMoviesUrl: 'https://api.themoviedb.org/3/search/movie',
      apiTvsUrl:    'https://api.themoviedb.org/3/search/tv',
      moviesFromApi: [],
      tvSeriesFromApi: [],

    }
  },
}
</script>

<style lang="scss">
</style>
