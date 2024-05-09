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
     })
     axios.get("https://api.themoviedb.org/3/search/tv", {
       params: paramsobj,
     }).then((resp) => {
     this.store.tvSeriesList = resp.data.results;
       console.log(this.store.tvSeriesList);
    });
    },
    
    }
    };
</script>

<template>
    <nav class="navbar bg-body-tertiary p-0">
        <div class="container-fluid bg-boolflix">
            <a class="navbar-brand">
                <img src="../assets/img/logo_boolflix.png" alt="">
            </a>
            <form class="d-flex" role="search">
               <AppSearchBar @filter="getMovie"/>
            </form>
        </div>
    </nav>
</template>

<style lang="scss" scoped>
.bg-boolflix {
    background-color: #101010;
}

</style>