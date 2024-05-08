<script>
export default {
    props: {
        filmObj: Object,
    }
};
</script>

<template>
<div class="film-container">
    <img :src="`https://image.tmdb.org/t/p/w342${filmObj.poster_path}`" alt="">
</div>
</template>

<style>

</style>