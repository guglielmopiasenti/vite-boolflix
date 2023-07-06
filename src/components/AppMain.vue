<script>

import { store } from '../assets/data/store';
import ProductionCard from './ProductionCard.vue';

export default {
    components: { ProductionCard },
    data() {
        return { store }
    }
}

</script>

<template>
    <section id="movies">
        <h2>Movies</h2>
        <!-- Render ProductionCard component for each movie in store.movies -->
        <ProductionCard v-for="movie in store.movies" :key="movie.id" :item="movie" />
    </section>
    <section id="series">
        <h2>Series</h2>
        <!-- Render ProductionCard component for each serie in store.series -->
        <ProductionCard v-for="serie in store.series" :key="serie.id" :item="serie" />
    </section>
</template>


<style></style>
