<script>
import { store } from '../store.js';
import MovieCard from './MovieCard.vue'; 

export default {
    // name: 'AppMoviesList', Questo non serve piu' nella versione vue corrente
    
    components: {
        MovieCard,
    },
    
    data(){
        return {
            store,
            
        };
    }
}
</script>

<template>
    <div class="container">
        <h1>Movies</h1>
        <div class="row">
            <MovieCard v-for="movie in store.movies" :key="movie.id" :cardInfo="movie"></MovieCard>
        </div>
    </div>
    
</template>

<style scoped lang="scss">
@use'../style/partials/_variables' as *;

.container {
    padding-top:10px;
    padding-bottom:10px;
    background-color: aqua;
}

.row {
    margin-left: -10px;
    margin-right: -10px;
    display: flex;
    flex-wrap: wrap;
}

</style>