<script>
import { store } from "../store";
export default {
    props: {
        filmObj: Object
    }
};
</script>

<template>
    <img :src="`https://image.tmdb.org/t/p/w342${filmObj.poster_path}`" alt="">
</template>

<style>

</style>