<script>


export default {
    // name: 'MovieCard',   Questo non serve piu' nella versione vue corrente
    
    /* CharacterCard accetta un oggetto che chiamo MovieInfo */
    
    props: {
        cardInfo: Object
    },

    data() {
      return {
        imageBasicUrl: 'https://image.tmdb.org/t/p/',
        ImagecardSizeUrl: 'w342',
        hovered: false,  // gestisce l'hover del mouse sulle immagini
        stars: ['starOne','starTwo', 'starThree', 'starFour', 'starFive'], //Gestisce il numero totale di stelle per il voto
      };
    },

    methods: {
        getImageUrl(name) {
            return new URL(`../assets/img/${name}`, import.meta.url).href;
        },

    },
    mounted() {
       
    }
}
    
</script>

<template>
    <!-- se il mouse non e' sopra l'elemento viene mostrata l'immagine -->
    <div v-if="!hovered" @mouseover="hovered = true" class="movie-card movie-card-cover">
        <div class="image-container">
            <img :src="`${imageBasicUrl}${ImagecardSizeUrl}${cardInfo.poster_path}`" alt="">
        </div>
    </div>
    <!-- se il mouse e' sopra l'elemento viene mostrata la descrizione -->
    <div v-else @mouseleave="hovered = false" class="movie-card movie-card-info">
        <ul>  
            <!-- Titolo -->
            <li>
                <ul>
                    <li>Titolo:</li> 
                    <!-- se cardInfo.title esiste (film) stampo cardInfo.title altrimenti stampo cardInfo.name (tv series) -->
                    <li>{{ cardInfo.title ? cardInfo.title : cardInfo.name }}</li>
                </ul>
            </li>
            
            <!-- Titolo originale -->
            <li>
                <ul>
                    <li>Titolo Originale:</li> 
                    <li>{{ cardInfo.original_title ? cardInfo.original_title : cardInfo.original_name }}</li>
                </ul>
            </li>
            <!-- Lingua -->
            <li v-if="cardInfo.original_language == 'en'" class="language">
                <ul>
                    <li>Lingua:</li> 
                    <li><img class="flag-image" :src="getImageUrl('english-flag.png')" alt=""></li>
                </ul>
            </li>
            <li v-else-if="cardInfo.original_language == 'fr'" class="language">
                <ul>
                    <li>Lingua:</li> 
                    <li><img class="flag-image" :src="getImageUrl('french-flag.png')" alt=""></li>
                </ul>
            </li>
            <li v-else-if="cardInfo.original_language == 'de'" class="language">
                <ul>
                    <li>Lingua:</li> 
                    <li><img class="flag-image" :src="getImageUrl('german-flag.png')" alt=""></li>
                </ul>
            </li>
            <li v-else-if="cardInfo.original_language == 'it'" class="language">
                <ul>
                    <li>Lingua:</li> 
                    <li><img class="flag-image" :src="getImageUrl('italian-flag.png')" alt=""></li>
                </ul>
            </li>
            <li v-else class="language">
                <ul>
                    <li>Lingua:</li> 
                    <li>{{ cardInfo.original_language }}</li>
                </ul>
            </li>
            <!-- Voto -->
            <li>
                <ul>
                    <li>Voto:</li> 
                    <!-- Stelle Voto -->
                    <li class="stars-container">
                        <template v-for="(star,index) in stars" >
                            <i v-if="index < Math.ceil((cardInfo.vote_average) / 2)" class="fa-solid fa-star"></i>
                            <i v-else class="fa-regular fa-star"></i>
                        </template>
                    </li>
                </ul> 
            </li>
            <!-- Overview -->
            <li class="overview">
                <ul>
                    <li>Overview</li>
                    <li>{{cardInfo.overview}}</li>
                </ul>
            </li>
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
            margin: 5px 0;

           .flag-image
           {
            width: 50%;
           } 
        }
    }
}

.image-container {
    width: 100%;
    height: 100%;
    

    img {
        width: 100%;
            
    }
}
.stars-container {
    color: yellow;
    display: flex; 
    flex-wrap: wrap;
 }

</style>