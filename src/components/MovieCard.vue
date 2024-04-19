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
        
        decimalToFive(numberToTransform) {
            /* trasforma il voto da 0 a 10 in un numero intero da 0 a 5  */
            const voteToFivecardInfo = Math.ceil(numberToTransform / 2);
            
        }

    },
    mounted() {
       this.decimalToFive();
    }
}
    
</script>

<template>
    <div class="movie-card">
        <ul>
            <li v-if="cardInfo.original_title"><span>Titolo:</span> <span>{{ cardInfo.original_title }}</span></li>
            <li v-else><span>Titolo:</span> <span>{{ cardInfo.original_name }}</span></li>
            <li><span>Titolo Originale:</span> <span>{{ cardInfo.original_title }}</span></li>
            <li v-if="cardInfo.original_language == 'en'" class="language"><span>Lingua:</span> <span><img class="flag-image" :src="getImageUrl('english-flag.png')" alt=""></span></li>
            <li v-else-if="cardInfo.original_language == 'fr'" class="language"><span>Lingua:</span> <span><img class="flag-image" :src="getImageUrl('french-flag.png')" alt=""></span></li>
            <li v-else-if="cardInfo.original_language == 'de'" class="language"><span>Lingua:</span> <span><img class="flag-image" :src="getImageUrl('german-flag.png')" alt=""></span></li>
            <li v-else-if="cardInfo.original_language == 'it'" class="language"><span>Lingua:</span> <span><img class="flag-image" :src="getImageUrl('italian-flag.png')" alt=""></span></li>
            <li v-else class="language"><span>Lingua:</span> <span>{{ cardInfo.original_language }}</span></li>
            <li><span>Voto:</span> <span>{{ cardInfo.vote_average }}</span> </li>
            <li><span>Voto:</span> <span class="stars-container" v-for="(star,index) in stars"><i class="fa-regular fa-star"></i></span> </li>
            <li><span>Voto:</span> <span>{{ cardInfo.vote_average }} <i class="fa-solid fa-star"></i></span> </li>
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
            margin: 10px 0;

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
    
}

</style>