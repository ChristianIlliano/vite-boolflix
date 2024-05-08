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
    <div class="row">
        <div class="col-2" v-for="curFilm in store.movieList">
            <AppFilmCard :filmObj="curFilm"/>
        </div>
    </div>
</template>

<style lang="scss" scoped></style>