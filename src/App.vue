<script>
import axios from 'axios';
import { store } from './store.js';
import AppFilter from './components/AppFilter.vue';
import AppMoviesList from './components/AppMoviesList.vue';
import AppTvList from './components/AppTvList.vue';
import AppHero from './components/AppHero.vue';


export default {
    components: {
      AppFilter,
      AppMoviesList,
      AppTvList,
      AppHero,
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
      
      getTvFromApi() {
        let apiUrl = 'https://api.themoviedb.org/3/search/tv';

        const queryParams = {
          api_key: store.api_key,
        };
        
        if(store.searchedName !== '') {
          queryParams.query = store.searchedName;
        }
        // Prende i movie dall'api e popola lo store
        axios.get(apiUrl, {
          params: queryParams
        })
        .then((response) => {
          store.tvShows = response.data.results;
        })
        
      },
    },
    mounted () {
      
    }
  }

</script>

<template>
  <AppFilter @searchPerformed="getMoviesFromApi(),getTvFromApi()"></AppFilter>
  <main>
    <AppHero></AppHero>
    <AppMoviesList></AppMoviesList>
    <AppTvList></AppTvList>
  </main>
</template>

<style lang="scss">
@use'./style/generic';
@use'./style/partials/_variables' as *;
main {
  background-color: $brand-primary;
  height: calc(100vh - 70px);
}
</style>
