<script>
import axios from "axios";
import AppHeader from "./components/AppHeader.vue";
import AppMain from "./components/AppMain.vue";
import { store } from "./store";

export default {
  components: {
    AppHeader,
    AppMain,
  },

  data() {
    return {
      store,
    };
  },

  created() {
    this.getMovie()
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
  <AppHeader @filter="getMovie"/>
  <AppMain />
</template>

<style lang="scss" scoped></style>