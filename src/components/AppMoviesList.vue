<script>
import { store } from '../store.js';
    
export default {
    name: 'AppMoviesList',
    data(){
        return {
            store,
            
        };
    }
}
</script>

<template>
    <div class="container">
        <h1>sono AppMoviesList</h1>
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