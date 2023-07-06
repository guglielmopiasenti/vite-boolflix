<script>
import SearchBar from './SearchBar.vue';
import { store } from '../assets/data/store';
import axios from 'axios';

export default {
    components: { SearchBar },
    data() {
        return {
            store,
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

    <section id="movies">
        <h2>Movies</h2>
        <ul v-for="movie in store.movies">
            <li>{{ movie.title }}</li>
            <li>{{ movie.original_title }}</li>
            <li>{{ movie.original_language }}</li>
            <li>{{ movie.vote_average }}</li>
        </ul>
    </section>
</template>

<style></style>
