<script>
import { store } from '../store.js';
import MovieCard from './MovieCard.vue';

export default {
    // name: 'AppMoviesList', Questo non serve piu' nella versione vue corrente

    components: {
        MovieCard,
    },

    data() {
        return {
            store,

        };
    }
}
</script>

<template>
    <section v-if="store.movies.length > 0" class="movies-section">
        <div class="container">
            <h2>Movies</h2>
            <div class="row">
                <MovieCard v-for="movie in store.movies" :key="movie.id" :cardInfo="movie"></MovieCard>
            </div>
        </div>
    </section>


</template>

<style scoped lang="scss">
@use'../style/partials/_variables' as *;


.movies-section {
    background-color: $brand-secondary;
}

.container {
    padding-top: 10px;
    padding-bottom: 10px;
    background-color: transparent;
}

.row {
    margin-left: -10px;
    margin-right: -10px;
    display: flex;
    flex-wrap: wrap;
}
</style>