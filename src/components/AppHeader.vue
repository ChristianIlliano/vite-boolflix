<script>
import { store } from "../store";
export default {
    
data() {
return {
    store,
}
},

methods: {

},
};
</script>

<template>
    <nav class="navbar bg-body-tertiary">
  <div class="container-fluid">
    <a class="navbar-brand">Navbar</a>
    <form class="d-flex" role="search">
      <input class="form-control me-2" type="search" placeholder="Search" aria-label="Search" v-model="store.userQuery">
      <button class="btn btn-outline-success" type="submit" @click="$emit('filter')">Search</button>
    </form>
  </div>
</nav>
</template>

<style lang="scss" scoped></style>