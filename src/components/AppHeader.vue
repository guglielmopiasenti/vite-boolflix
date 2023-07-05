<script>
const endpoint = 'https://api.themoviedb.org/3/search/movie?api_key=417ff78debed7617bb96dc46540a0f3d';
import SearchBar from './SearchBar.vue';
import AppButton from './AppButton.vue';

export default {
    components: { SearchBar, AppButton },
    data() {
        return {
            moviesFilter: ''
        }
    },
    methods: {
        onTermChange(term) {
            this.moviesFilter = term;
        },
        searchMovies() {
            const filterEndpoint = `${endpoint}&query=${this.moviesFilter}`;
            console.log(filterEndpoint);
        },
    },
}

</script>

<template>
    <SearchBar placeholder="Search for a movie or tv series..." @term-change="onTermChange" @search-submit="searchMovies" />
</template>

<style></style>
