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
    <div class="container">
        <div class="logo-container">
            <img src="" alt="logo">
        </div>
        <div class="searchbar-container">
            <input type="text" placeholder="Search movie">
        </div>
        <div class="button-container">
            <button>Search</button>
        </div>
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
}



</style>