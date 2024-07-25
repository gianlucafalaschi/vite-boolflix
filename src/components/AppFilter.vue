<script>
import { store } from '../store.js';
    
export default {
   // name: 'AppFilter',  Questo non serve piu' nella versione vue corrente
    data(){
        return {
            store,


            
        };
    },
    methods: {
        /* Funzione che pulisce il campo input della ricerca del film */
        cleanSearchBox() {
            store.searchedName = '';
        },
        /* Funzione che svuota i risultati della ricerca nello store */
        cleanSearchResults() {
            store.movies = [];
            store.tvShows = [];
        }

    },
}
</script>

<template>
    <header>
        <div class="container">
            <div class="logo-container" @click="cleanSearchResults">
                <h1>BOOLFIX</h1>
            </div>
            <div class="research">
                <input class="search-input" type="text" placeholder="Search movie" v-model="store.searchedName">
                <!-- Quando il pulsante viene premuto emette un evento chiamato searchPerformed, 
                    inoltre chiama la funzione cleanSearchBox() che pulisce il box dell'input  -->
                <button class="search-button" @click="$emit('searchPerformed'), cleanSearchBox()">Search</button>
            </div>
        </div>
    </header>
    
    
</template>

<style scoped lang="scss">
@use'../style/partials/_variables' as *;


header {
    background-color: $brand-primary;
}

.container {
    display: flex;
    justify-content: space-between;
    align-items: center;
    gap: 10px;
    background-color: $brand-primary;
    padding-top:10px;
    padding-bottom:10px;
    height: 70px;
}

.logo-container {
    color:$brand-tertiary;
    cursor: pointer;
}

.research {
    display: flex;
    gap: 10px;
}

.search-input {
    padding: 6px 8px;
    border-radius: 5px;
    border: none;
}

.search-button {
    padding:6px 8px;
    color: white;
    background-color: #E50914;
    font-weight: bold;
    border: none;
    border-radius: 5px;
    cursor: pointer;
}
</style>