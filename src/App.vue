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
        let apiUrl = 'https://api.themoviedb.org/3/search/movie';

        const queryParams = {
          api_key: '69f2eb4c4173464dd2ce2e21bf0b9476',
          /* query: 'ritorno', */
        };

        if(store.searchedName !== '') {
          queryParams.query = store.searchedName;
        }
        // Prende i movie dall'api e popola lo store
        axios.get(apiUrl, {
        params: queryParams
      })
      .then((response) => {
        store.movies = response.data.results;
      }); 
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
