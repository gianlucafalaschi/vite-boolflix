<script>
import axios from 'axios';
import { store } from './store.js';
import AppFilter from './components/AppFilter.vue';
import AppMoviesList from './components/AppMoviesList.vue';

export default {
    components: {
      AppFilter,
      AppMoviesList,
    },
    data() {
      return {
        store,
      };
    },
    methods: {
      getMoviesFromApi() {
        alert('chiamata getMoviesFromApi');
      },
    },
    mounted () {

    }
  }

</script>

<template>
  <AppFilter @searchPerformed="getMoviesFromApi()"></AppFilter>
  <AppMoviesList></AppMoviesList>
</template>

<style lang="scss">
@use'./style/generic';
</style>
