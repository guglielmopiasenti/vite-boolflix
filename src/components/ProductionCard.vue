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
        }
    }
}
</script>

<template>
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
        <!-- Display vote average of the item -->
        <li>{{ item.vote_average }}</li>
    </ul>
</template>
<style></style>