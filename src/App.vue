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
    getPopular(){
      axios.get(`${this.apiPopularMoviesUrl}?api_key=${this.apiKey}&include_adult=false&language=it`)
        .then((result) => {
          this.moviesFromApi = result.data.results;
        })
        .catch((error) => {
          console.warn(error);
        })

      axios.get(`${this.apiPopularTvsUrl}?api_key=${this.apiKey}&include_adult=false&language=it`)
        .then((result) => {
          this.tvSeriesFromApi = result.data.results;
        })
        .catch((error) => {
          console.warn(error);
        })
    },
    searchFilmAndTvSeries(needle) {
      if(needle!="")
      {
        axios.get(`${this.apiMoviesUrl}?api_key=${this.apiKey}&query=${needle}&include_adult=false&language=it`)
          .then((result) => {
            this.moviesFromApi = result.data.results;
          })
          .catch((error) => {
            console.warn(error);
          })
  
        axios.get(`${this.apiTvsUrl}?api_key=${this.apiKey}&query=${needle}&include_adult=false&language=it`)
          .then((result) => {
            this.tvSeriesFromApi = result.data.results;
          })
          .catch((error) => {
            console.warn(error);
          })
      }
      else
      {
        this.getPopular();
      }
    },
  },
  mounted() {
    this.getPopular();
  },
  data: function () {
    return {

      apiKey: '8b59d4e5705275542674ad47f794ccf6',
      apiMoviesUrl: 'https://api.themoviedb.org/3/search/movie',
      apiTvsUrl:    'https://api.themoviedb.org/3/search/tv',
      apiPopularMoviesUrl: 'https://api.themoviedb.org/3/movie/popular',
      apiPopularTvsUrl:    'https://api.themoviedb.org/3/tv/popular',
      moviesFromApi: [],
      tvSeriesFromApi: [],

    }
  },
}
</script>

<style lang="scss">
 @import "~bootstrap/scss/bootstrap.scss";
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
</style>
