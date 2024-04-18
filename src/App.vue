<script>
import axios from 'axios';
import { store } from './store.js';
import AppFilter from './components/AppFilter.vue';
import AppMoviesList from './components/AppMoviesList.vue';
import AppTvList from './components/AppTvList.vue';

export default {
    components: {
      AppFilter,
      AppMoviesList,
      AppTvList,
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
          api_key: store.api_key,
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
  <main>
    <AppMoviesList></AppMoviesList>
    <AppTvList></AppTvList>
  </main>
  
</template>

<style lang="scss">
@use'./style/generic';
</style>
