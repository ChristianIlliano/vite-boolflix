<script>
import { store } from "../store";
export default {
    
data() {

},

methods: {
movieList() {
    axios.get("https://api.themoviedb.org/3/search/movie", {
        params: {
            api_key: this.store.api_key
        }
    })
}
},
};
</script>

<template>
    <nav class="navbar bg-body-tertiary">
  <div class="container-fluid">
    <a class="navbar-brand">Navbar</a>
    <form class="d-flex" role="search">
      <input class="form-control me-2" type="search" placeholder="Search" aria-label="Search">
      <button class="btn btn-outline-success" type="submit" @click="$emit('filter')">Search</button>
    </form>
  </div>
</nav>
</template>

<style lang="scss" scoped></style>