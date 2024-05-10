<script>
import { store } from "../store";
export default {
    props: {
        filmObj: Object
    },

    methods: {
        showLanguage(curFlag) {
            let imgUrl = ""
            switch (curFlag) {
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

        votation(vote) {
            vote = Math.floor(vote / 2) + 1
            // ------------------------
            if (vote < 0) {
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
    <div class="card-container">
        <div class="poster">
            <img :src="`https://image.tmdb.org/t/p/w500${filmObj.poster_path}`" alt="">
        </div>

        <div class="info-card">

            <h4>{{ filmObj.title }}</h4>
            <p>{{ filmObj.original_title }}</p>

        
                <div class="icon-language">
                    <img :src="showLanguage(filmObj.original_language)" alt=""
                        v-if="showLanguage(filmObj.original_language) != 'Bandiera non disponibile'">
                    <p v-else>{{ showLanguage(filmObj.original_language) }}</p>
                </div>
                <div class="star-vote">
                    <p v-for="curStar in votation(filmObj.vote_average)">
                        <i class="fa-solid fa-star"></i>
                    </p>
                    <p v-for="curStar in (5 - votation(filmObj.vote_average))">
                        <i class="fa-regular fa-star"></i>
                    </p>
                </div>
                <p>{{ filmObj.vote_average }}</p>

                <div class="scroll-text ">
                    <p>
                        {{ filmObj.overview }}
                    </p>
                </div>
            </div>

        </div>
</template>

<style lang="scss" scoped>
.icon-language {
    img {
        width: 100%;
        height: 100%;
        max-width: 30px
    }
}

;

.star-vote {
    display: flex;
    font-size: 5rem;
}

.card-container {
    position: relative;
    height: 100%;
    width: 100%;
    margin: 20px;

    p {
        font-size: 1.6rem;
        margin-bottom: 10px;
    }

    .poster {
        position: relative;
        z-index: -1;
    }

    .info-card {
        display: flex;
        /* transform: rotateY(180deg); */
        flex-direction: column;
        background-color: #101010;
        color: white;
        padding: 10px;
        opacity: 0;
        position: absolute;
        top: 0;
        left: 0;
        height: 100%;
        width: 100%;
        overflow: scroll;
        scrollbar-width: none;

        span {
            font-size: 1.4rem;
            display: block;
        }

        h4 {
            font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
            font-size: 2rem;
        }

        scroll-text {
            overflow: scroll;
            scrollbar-width: none;
        }

    }

    .poster img {
        width: 100%;
        height: 100%;
        border-radius: 5px;

    }

    &:hover {
        .poster {
            /* transform: rotateY(180deg); */
            transition: 1s;
            opacity: 0;
        }

        .info-card {
            /* transform: rotateY(360deg); */
            opacity: 1;
            transition: 1s;
        }
    }
}
</style>