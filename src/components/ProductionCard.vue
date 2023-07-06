<script>
export default {
    props: {
        item: Object
    },
    computed: {
        hasFlag() {
            const availableFlags = ['it', 'en'];
            return availableFlags.includes(this.item.original_language);
        },
        flagSrc() {
            const url = new URL(`../assets/img/${this.item.original_language}.png`, import.meta.url);
            return url.href;
        },
        imagePath() {
            const url = new URL(`https://image.tmdb.org/t/p/w342/${this.item.backdrop_path}`);
            return url.href;
        },
        voteRating() {
            // Convert the vote average from 1-10 to an integer from 1-5
            return Math.ceil(this.item.vote_average / 2);
        }
    }
}
</script>

<template>
    <img :src="imagePath" alt="">
    <ul>
        <!-- Display title or name of the item -->
        <li>{{ item.title || item.name }}</li>
        <!-- Display original title or name of the item -->
        <li>{{ item.original_title || item.original_name }}</li>
        <li>
            <!-- Display flag image if language is available -->
            <img v-if="hasFlag" :src="flagSrc" :alt="item.original_language">
            <!-- Display original language if flag is not available -->
            <span v-else> {{ item.original_language }}</span>
        </li>
        <!-- Display the vote rating as a number of full stars -->
        <li>
            <span v-for="n in 5" :key="n"
                :class="{ 'fa fa-star': n <= voteRating, 'fa-regular fa-star': n > voteRating }"></span>
        </li>
    </ul>
</template>
<style></style>\