<script>
import { store } from "../store";
export default {
    // emits: ["filter"],
    data() {
        return {
            store
        }
    }
};
</script>

<template>
    <input type="text" v-model="this.store.userQuery" placeholder="Es: Harry Potter">
    <input type="button" value="Search" @click="$emit('filter')">
</template>