<script>

import { store } from '../assets/data/store';

export default {
    data() {
        return { store }
    }
}

</script>

<template>
    <section id="movies">
        <h2>Movies</h2>
        <ul v-for="movie in store.movies " :key='movie.id'>
            <li>{{ movie.title }}</li>
            <li>{{ movie.original_title }}</li>
            <li>{{ movie.original_language }}</li>
            <li>{{ movie.vote_average }}</li>
        </ul>
    </section>
    <section id="series">
        <h2>Series</h2>
        <ul v-for="serie in store.series " :key='serie.id'>
            <li>{{ serie.name }}</li>
            <li>{{ serie.original_name }}</li>
            <li>{{ serie.original_language }}</li>
            <li>{{ serie.vote_average }}</li>
        </ul>
    </section>
</template>

<style></style>
