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
        <div class="row">
            <div v-for="tvShow in store.tvShows">Qui va una moviecard</div>
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