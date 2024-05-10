<script>
import AppFilmCard from "./AppFilmCard.vue";
import { store } from "../store";
export default {
    components: {
        AppFilmCard,
    },
    data() {
        return {
            store,
        }
}
};
</script>

<template>
    <div class="row p-5 d-flex justify-content-center align-items-center">
        <h1>Film</h1>
        <div class="col-2 m-2" v-for="curFilm in this.store.movieList">
            <AppFilmCard :filmObj="curFilm"/>
        </div>
    </div>

    <div class="row p-5">
        <h1>Serie Tv</h1>
        <div class="col-2" v-for="curSeries in this.store.tvSeriesList">
            <AppFilmCard :filmObj="curSeries"/>
        </div>
    </div>
</template>

<style lang="scss" scoped></style>