<script>
import { store } from '../store.js';
import MovieCard from './MovieCard.vue'; 

export default {
    name: 'AppTvList',
    
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
        <h2>TV Series</h2>
        <div class="row">
            <MovieCard v-for="tvShow in store.tvShows" :cardInfo="tvShow">Qui va una moviecard</MovieCard>
        </div>
    </div>
    
</template>

<style scoped lang="scss">
@use'../style/partials/_variables' as *;

.container {
    padding-top:10px;
    padding-bottom:10px;
    background-color: beige;
}

.row {
    margin-left: -10px;
    margin-right: -10px;
    display: flex;
    flex-wrap: wrap;
}

</style>