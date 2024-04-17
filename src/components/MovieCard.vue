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
            <li><span>Titolo:</span> <span>{{ movieInfo.original_title }}</span></li>
            <li><span>Titolo Originale:</span> <span>{{ movieInfo.original_title }}</span></li>
            <li><span>Lingua:</span> <span>{{ movieInfo.original_language }}</span></li>
            <li><span>Voto:</span> <span>{{ movieInfo.vote_average }}</span> </li>
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
            display: flex;
            flex-direction: column;
            margin: 10px 0;

            
        }
    }
}

</style>