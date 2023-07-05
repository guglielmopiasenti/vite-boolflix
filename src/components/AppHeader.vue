<script>

import SearchBar from './SearchBar.vue';
import AppButton from './AppButton.vue';

export default {
    components: { SearchBar, AppButton },
    data() {
        return {
            nameFilter: ''
        }
    },
    methods: {
        onTermChange(term) {
            this.nameFilter = term;
        },
        searchMovies() {

        }
    },
}

</script>

<template>
    <SearchBar placeholder="Search for a movie or tv series..." @term-change="onTermChange" @search-submit="searchMovies" />
</template>

<style></style>
