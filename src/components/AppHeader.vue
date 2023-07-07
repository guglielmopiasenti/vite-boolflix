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
        <div class="d-flex align-items-center">
            <img src="../assets/img/Netflix-logo-red-black-png.png" alt="netflix logo">
            <ul class="d-flex text-white gap-3 mt-2">
                <li>Home</li>
                <li>TV Shows</li>
                <li>Movies</li>
                <li>Recently Added</li>
                <li>My List</li>
            </ul>
        </div>
        <div class="d-flex align-items-center">
            <SearchBar placeholder="Search for a movie or tv series..." @term-change="onTermChange"
                @search-submit="searchMovies" />
            <img class="user-img" src="../assets/img/Netflix-avatar.png" alt="">
            <i class="fa-solid fa-sort-down"></i>
        </div>
    </header>
</template>

<style lang="scss" scoped>
header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    background-color: black;


    img {
        height: 100px;
        margin-left: 20px;
    }

    .user-img {
        height: 40px;
        border-radius: 5px;
        margin-left: 40px;
    }

    i {
        margin-right: 40px;
        margin-left: 10px;
        color: white;
    }
}
</style>
