<script>


export default {
    // name: 'MovieCard',   Questo non serve piu' nella versione vue corrente
    
    /* CharacterCard accetta un oggetto che chiamo MovieInfo */
    
    props: {
        cardInfo: Object
    },

    data() {
      return {
        supportedFlags:[
            'it',
            'en',
            'fr',
            'de'
        ],
        imageBasicUrl: 'https://image.tmdb.org/t/p/',
        ImagecardSizeUrl: 'w342',
        hovered: false,  // gestisce l'hover del mouse sulle immagini
        starsFull: [], // Array inizialmente vuoto che gestisce il numero totale di stelle piene per il voto
        starsEmpty: [], // Array inizialmente vuoto che gestisce il numero totale di stelle vuote per il voto
      };
    },

    methods: {
        
        getFlagUrl(){
            /* crea una variabile usando l'original language ricavato dalla API + .png */
            let flagImageName = this.cardInfo.original_language + '.png';
            /* Usa questa variabile nella funzione che
            permette di usare l'url delle immagini salvete in locale quando usate dinamicamente */
            return new URL(`../assets/img/${flagImageName}`, import.meta.url).href;
        },
        getStars() {   
            /* Funzione che determina il numero di stelle per il voto */
            for (let i = 0; i < 5; i++) {
                /* se l'indice i e minore del voto 1 a 10 (diviso 2 e arrotondato per eccesso)
                allora pusha un elemento nell'array starsFull */
                if (i < Math.ceil((this.cardInfo.vote_average) / 2)) {
                    this.starsFull.push('starFull');
                    /* altrimenti pusha un elemento nell'array starsEmpty */
                } else {
                    this.starsEmpty.push('starEmpty');
                }
            };
        }
    },
    mounted() {
       this.getStars()
    }
}
    
</script>

<template>
    <!-- se il mouse non e' sopra l'elemento viene mostrata l'immagine -->
    <div v-if="!hovered" @mouseover="hovered = true" class="movie-card movie-card-cover">
        <div class="image-container">
            <!-- se l'immagine e'presente nell'Api viene stampata -->
            <img v-if="cardInfo.poster_path" :src="`${imageBasicUrl}${ImagecardSizeUrl}${cardInfo.poster_path}`" alt="">
            <!-- altrimenti se l'immagine non e' presente nell'Api -->
            <div v-else class="missing-image">
                <!-- se title e' presente nell'Api (film) viene stampato, altrimenti viene 
                    stampato name (serieTv) -->
                <div>{{cardInfo.title ? cardInfo.title : cardInfo.name}}</div>
                <div>Image not available</div>
            </div>
        </div>
    </div>
    <!-- se il mouse e' sopra l'elemento viene mostrata la descrizione -->
    <div v-else  @mouseleave="hovered = false" class="movie-card movie-card-info">
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
            <li>
                <ul>
                    <li>Lingua:</li>
                    <!-- se l'array delle lingue supportate include la lingua ricavata dall'Api per original_language
                    stampo l'immagine con src ricavato dalla funzione getFlagUrl() -->
                    <li v-if="supportedFlags.includes(cardInfo.original_language)"><img class="flag-image" :src="getFlagUrl()" alt=""></li>
                    <!-- Altrimenti stampo il testo dell'original language ricavato dall'Api -->
                    <li v-else>{{ cardInfo.original_language }}</li>
                </ul>
            </li>
            <!-- Voto -->
            <li>
                <ul>
                    <li>Voto:</li> 
                    <!-- Stelle Voto -->
                    <li class="stars-container">
                        <!-- stampa in font awesome (stella piena) per ogni elemento nell'array starsFull  -->
                        <i v-for="elementStarFull in starsFull" class="fa-solid fa-star"></i>
                        <!-- stampa in font awesome (stella piena) per ogni elemento nell'array starsEmpty  -->
                        <i v-for="elementStarEmpty in starsEmpty" class="fa-regular fa-star"></i>
                    </li>
                </ul> 
            </li>
            <!-- Overview -->
            <li class="overview">
                <ul>
                    <li>Overview</li>
                    <li class="overview-text">{{cardInfo.overview}}</li>
                </ul>
            </li>
        </ul>
    </div>
</template>

<style scoped lang="scss">
@use'../style/partials/_variables' as *;





.movie-card-cover, .movie-card-info {
    /* width: calc((100% / 6) - 12px); */
    width: 100%;
    max-height: 300px;
    border: 1px solid white;
    background-color: black;
    padding: 10px;
    margin: 6px 6px;
    overflow-y: auto;

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
    
    .missing-image {
        color: white;
        display: flex;
        flex-direction: column;
        align-items: center;
        gap: 10px;
        
    }

    img {
        width: 100%;
            
    }
}
.stars-container {
    color: yellow;
    display: flex; 
    flex-wrap: wrap;
 }



/* MEDIA QUERIES */

/*----------------
    COLUMNS per XS > 0px
-----------------*/


/*----------------
    COLUMNS per SM >= 576px
-----------------*/
@media screen and (min-width: 576px) {

    .movie-card-cover, .movie-card-info {
        width: calc((100% / 2) - 12px);
    }

}

/*----------------
COLUMNS per MD >= 768px
-----------------*/
@media screen and (min-width: 768px) {

.movie-card-cover, .movie-card-info {
    width: calc((100% / 4) - 12px);
    }

}
/*----------------
COLUMNS per LG >= 992px
-----------------*/
@media screen and (min-width: 992px) {

    .movie-card-cover, .movie-card-info {
    width: calc((100% / 6) - 12px);
    }

}

</style>