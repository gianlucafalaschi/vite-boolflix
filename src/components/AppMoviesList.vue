<script>
import { store } from '../store.js';
import MovieCard from './MovieCard.vue'; 

export default {
    name: 'AppMoviesList',
    
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
        <MovieCard></MovieCard>
    </div>
    
</template>

<style scoped lang="scss">
@use'../style/partials/_variables' as *;

.container {
    display: flex;
    gap: 10px;
    background-color: pink;
    padding-top:10px;
    padding-bottom:10px;
    background-color: aqua;
}

</style>