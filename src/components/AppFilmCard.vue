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
        }
    }
};
</script>

<template>
    <div>
    <img :src="`https://image.tmdb.org/t/p/w342${filmObj.poster_path}`" alt="">
    <h2>{{ filmObj.title }}</h2>
    <p>{{ filmObj.original_title }}</p>
    <div class="icon-language">
        <img :src="showLanguage(filmObj.original_language)" alt=""
        v-if="showLanguage(filmObj.original_language) != 'Bandiera non disponibile'">
        <p v-else>{{showLanguage(filmObj.original_language)}}</p>
        <p>{{ filmObj.original_language }}</p>
    </div>
    <p>{{ filmObj.vote_average }}</p>
    </div>
</template>

<style>
.icon-language {
    img {
        max-width: 30px;
    }
}
</style>