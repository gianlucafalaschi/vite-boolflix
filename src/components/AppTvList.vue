<script>
import { store } from '../store.js';
import MovieCard from './MovieCard.vue';

export default {
    // name: 'AppTvList',  Questo non serve piu' nella versione vue corrente

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
    <section v-if="store.tvShows.length > 0" class="tv-series-section">
        <div class="container">
            <h2 class="title">TV Series</h2>
            <div class="row">
                <MovieCard v-for="tvShow in store.tvShows" :cardInfo="tvShow">Qui va una moviecard</MovieCard>
            </div>
        </div>
    </section>
</template>

<style scoped lang="scss">
@use'../style/partials/_variables' as *;


.tv-series-section {
    background-color:$brand-primary;
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

.title {
    color: white;
}
</style>