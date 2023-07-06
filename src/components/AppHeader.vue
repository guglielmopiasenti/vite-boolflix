<script>
const endpoint = 'https://api.themoviedb.org/3/search/movie?api_key=417ff78debed7617bb96dc46540a0f3d';
import SearchBar from './SearchBar.vue';
import AppButton from './AppButton.vue';
import { store } from '../assets/data/store';
import axios from 'axios';

export default {
    components: { SearchBar },
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
            if (!this.moviesFilter) {
                store.movies = [];
                return;
            };

            const { key, language, baseUri } = api

            const axiosConfig = {
                params: {
                    api_key: api.key,
                    query: this.moviesFilter,
                }
            }

            axios.get(`${baseUri}/search/movie`, axiosConfig)
                .then(res => {
                    store.movies = res.data.results
                })
        },
    },
}

</script>

<template>
    <SearchBar placeholder="Search for a movie or tv series..." @term-change="onTermChange" @search-submit="searchMovies" />
</template>

<style></style>
