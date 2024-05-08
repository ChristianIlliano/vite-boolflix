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
    <div>
        <div class="col p-2" v-for="curFilm in store.movieList">
            <AppFilmCard :filmObj="curFilm"/>
        </div>
    </div>
</template>

<style lang="scss" scoped></style>