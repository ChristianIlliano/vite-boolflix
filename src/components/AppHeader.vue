<script>
import axios from "axios";
import { store } from "../store";
import AppSearchBar from "./AppSearchBar.vue"
export default {

    data() {
        return {
            store,
        }
    },

    components: {
        AppSearchBar,
    },

    methods: {
        getMovie() {
      const paramsobj = {
                api_key: this.store.api_key,
                query: this.store.userQuery,
            }
      axios.get("https://api.themoviedb.org/3/search/movie", {
        params: paramsobj,
      }).then((resp) => {
      this.store.movieList = resp.data.results;
        console.log(this.store.movieList);
     });
    }
    }
    };
</script>

<template>
    <nav class="navbar bg-body-tertiary">
        <div class="container-fluid">
            <a class="navbar-brand">Navbar</a>
            <form class="d-flex" role="search">
               <AppSearchBar @filter="getMovie"/>
            </form>
        </div>
    </nav>
</template>

<style lang="scss" scoped></style>