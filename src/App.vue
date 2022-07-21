<template>
  <div id="app">
    <Header @search="searchFilm" />
    <Main />
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
          console.log(result.data);
        })
        .catch((error) => {
          console.warn(error);
        })
    }
  },
}
</script>

<style lang="scss">
</style>
