<script>
import { store } from "../store";
export default {
    props: {
        filmObj: Object
    },

    methods: {
        showLanguage(curFlag) {
            let imgUrl = ""
            switch(curFlag){
                case "en":
                    imgUrl = "../src/assets/img/united-kingdom.png"
                    break;
                case "it":
                    imgUrl = "../src/assets/img/italia.png"
                    break; 
                case "fr":
                    imgUrl = "../src/assets/img/francia.png"
                    break; 
                case "ja":
                    imgUrl = "../src/assets/img/japan.png"
                    break;
                default:
                    return "Bandiera non disponibile"   
            }
            return imgUrl
        },

        votation(vote){
            vote = Math.floor(vote / 2) + 1
            // ------------------------
            if (vote < 0){
                return 0
            } else if (vote > 5)
                return 5
            else {
                return vote
            }
        },
    }
};
</script> 

<template>
    <div>
    <img :src="`https://image.tmdb.org/t/p/w500${filmObj.poster_path}`" alt="">
    <h4>{{ filmObj.title }}</h4>
    <p>{{ filmObj.original_title }}</p>
    <div class="icon-language">
        <img :src="showLanguage(filmObj.original_language)" alt=""
        v-if="showLanguage(filmObj.original_language) != 'Bandiera non disponibile'">
        <p v-else>{{showLanguage(filmObj.original_language)}}</p>
        <div>
        <span v-for="curStar in votation(filmObj.vote_average)">
            <i class="fa-solid fa-star"></i>
        </span>
        <span v-for="curStar in (5 - votation(filmObj.vote_average))">
            <i class="fa-regular fa-star"></i>
        </span>
        </div>
    </div>
    <p>{{ filmObj.vote_average }}</p>
    </div>
</template>

<style>
.icon-language {
    img {
        max-width: 30px;
    }
};
</style>