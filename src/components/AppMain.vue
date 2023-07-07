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
    <div>
        <section id="productions-container" class="container py-5">
            <h2 v-if="store.movies.length || store.series.length">Movies</h2>
            <section id="movies">
                <!-- Render ProductionCard component for each movie in store.movies -->
                <ProductionCard v-for="movie in store.movies" :key="movie.id" :item="movie" />
            </section>
            <h2 v-if="store.movies.length || store.series.length">Series</h2>
            <section id="series">
                <!-- Render ProductionCard component for each serie in store.series -->
                <ProductionCard v-for="serie in store.series" :key="serie.id" :item="serie" />
            </section>
        </section>
    </div>
</template>


<style lang="scss" scoped>
div {
    background-color: #141414;
    min-height: 100vh;
}

h2 {
    color: white;
}

section {
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    gap: 25px;
}
</style>
