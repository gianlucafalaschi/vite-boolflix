<script>
import { store } from '../store.js';
    
export default {
    name: 'AppFilter',
    data(){
        return {
            store,
            
        };
    }
}
</script>

<template>
    <header>
        <div class="container">
            <div class="logo-container">
                <h1>BOOLFIX</h1>
            </div>
            <div class="research">
                <div class="searchbar-container">
                    <input type="text" placeholder="Search movie" v-model="store.searchedName">
                </div>
                <div class="button-container">
                    <button @click="$emit('searchPerformed')">Search</button>
                </div>
            </div>
        </div>
    </header>
    
    
</template>

<style scoped lang="scss">
@use'../style/partials/_variables' as *;

.container {
    display: flex;
    align-items: center;
    gap: 10px;
    background-color: pink;
    padding-top:10px;
    padding-bottom:10px;
}

.logo-container {
    color: #E50914;
}

.research {
    display: flex;
    
}

</style>