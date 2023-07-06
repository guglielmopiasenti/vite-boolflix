<script>
import SearchBar from './SearchBar.vue';

import { store } from '../assets/data/store'
export default {
    components: { SearchBar },
    emits: ['search-submit'],

    methods: {
        onTermChange(term) {
            store.titleFilter = term;

        },
        searchMovies() {
            this.$emit('search-submit');

        },
    },
}

</script>

<template>
    <header>
        <SearchBar placeholder="Search for a movie or tv series..." @term-change="onTermChange"
            @search-submit="searchMovies" />
    </header>
</template>

<style></style>
