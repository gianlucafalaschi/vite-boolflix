<script>


export default {
    name: 'MovieCard',
    /* CharacterCard accetta un oggetto che chiamo MovieInfo */
    
    props: {
        cardInfo: Object
    },

    data() {
      return {
        imageBasicUrl: 'https://image.tmdb.org/t/p/',
        ImagecardSizeUrl: 'w342',

        stars: ['starOne','starTwo', 'starThree', 'starFour', 'starFive'],
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
    <div class="movie-card">
        <ul>  
            <!-- Titolo -->
            <li v-if="cardInfo.title">
                <ul>
                    <li>Titolo:</li> 
                    <li>{{ cardInfo.title }}</li>
                </ul>
            </li>
            <li v-else>
                <ul>
                    <li>Titolo:</li> 
                    <li>{{ cardInfo.name }}</li>
                </ul>
            </li>
            <!-- Titolo originale -->
            <li v-if="cardInfo.original_title">
                <ul>
                    <li>Titolo Originale:</li> 
                    <li>{{ cardInfo.original_title }}</li>
                </ul>
            </li>
            <li v-else>
                <ul>
                    <li>Titolo Originale:</li> 
                    <li>{{ cardInfo.original_name }}</li>
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
                <span>Voto:</span> 
                <span v-for="(star,index) in stars" class="stars-container">
                    <i v-if="index < Math.ceil((cardInfo.vote_average) / 2)" class="fa-solid fa-star"></i>
                    <i v-else class="fa-regular fa-star"></i>
                </span> 
            </li>
        </ul>
        <div class="image-container">
            <img :src="`${imageBasicUrl}${ImagecardSizeUrl}${cardInfo.poster_path}`" alt="">
        </div>
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
    background-color:coral;
    
}

</style>