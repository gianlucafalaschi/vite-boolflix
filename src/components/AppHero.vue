<script>
import { store } from '../store.js';


export default {
    // name: 'AppTvList',  Questo non serve piu' nella versione vue corrente

    components: {

    },

    data() {
        return {
            store,

        };
    }
}
</script>

<template>
    <section v-if="store.tvShows.length < 1 || store.tvShows.length < 1" class="hero">
        <div class="container">
            <div class="row">
                <div class="background-img-container">
                    <div class="text">
                        <h1 class="title">Unlimited movies and TV shows</h1>
                        <h2 class="subtitle">Find your favourite Movies and Series</h2>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<style scoped lang="scss">
@use'../style/partials/_variables' as *;

.background-img-container {
    background-image: url('../assets/img/hero-img.jpg');
    background-position: center;
    background-size:cover;
    height: 400px;
    display: flex;
    align-items: center;
    justify-content: center;    
    
}

.text {
    background-color: rgba(0, 0, 0, 0.4 );
}

.title {
    color: white;
    text-align: center;
    font-size: 40px;
    margin-bottom: 40px;
    
}
.subtitle {
    color: white;
    text-align: center;
    font-size: 30px;
    
}

</style>