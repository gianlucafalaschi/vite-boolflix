<script>


export default {
    name: 'MovieCard',
    /* CharacterCard accetta un oggetto che chiamo MovieInfo */
    
    props: {
        cardInfo: Object
    },

    data() {
      return {
        
      };
    },

    methods: {
        getImageUrl(name) {
            return new URL(`../assets/img/${name}`, import.meta.url).href;
        }

    },

}
    
</script>

<template>
    <div class="movie-card">
        <ul>
            <li><span>Titolo:</span> <span>{{ cardInfo.original_title }}</span></li>
            <li><span>Titolo Originale:</span> <span>{{ cardInfo.original_title }}</span></li>
            <li class="language"><span>Lingua:</span> <span>{{ cardInfo.original_language }}</span></li>
            <li class="language"><span>Lingua:</span> <span><img class="flag-image" :src="getImageUrl('english-flag.png')" alt=""></span></li>
            <li><span>Voto:</span> <span>{{ cardInfo.vote_average }}</span> </li>
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

           .flag-image
           {
            width: 50%;
           } 
        }
    }
}

</style>