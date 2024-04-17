<script>


export default {
    name: 'MovieCard',
    /* CharacterCard accetta un oggetto che chiamo MovieInfo */
    
    props: {
        movieInfo: Object
    }
}
</script>

<template>
    <div class="movie-card">
        <ul>
            <li>Titolo</li>
            <li>Titolo Originale</li>
            <li>Lingua</li>
            <li>Voto</li>
        </ul>
    </div>
</template>

<style scoped lang="scss">
@use'../style/partials/_variables' as *;





.movie-card {
    width: calc((100% / 6) - 12px);
    border: 1px solid white;
    background-color: black;
    padding: 10px;
    margin: 6px 6px;

    ul {
        color: white;
        list-style: none;

        li {
            margin: 10px 0;
        }
    }
}

</style>