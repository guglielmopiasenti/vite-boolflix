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
    },
    methods: {
        handleImageError(event) {
            // Update the source of the image to the default image path
            event.target.src = 'src/assets/img/Netflix-logo-red-black-png.png';
        },
    },
}
</script>

<template>
    <section id="card">
        <div class="image-container">
            <img :src="imagePath" alt="" class="prod-img" @error="handleImageError">
            <ul class="content">
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
        </div>
    </section>
</template>

<style lang="scss" scoped>
#card {
    position: relative;
}

.image-container {
    position: relative;
    display: flex;
}

.content {
    position: absolute;
    top: 0;
    left: 0;
    opacity: 0;
    visibility: hidden;
    transition: opacity 0.3s;
    background-color: rgba(0, 0, 0, 0.5);
    backdrop-filter: blur(5px);
    color: white;
    width: 100%;
    height: 100%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    text-align: center;
    gap: 10px;
    padding-right: 20px;
}


.image-container:hover .content {
    opacity: 1;
    visibility: visible;
}

li {
    img {
        height: 50px;
    }

    span {
        color: rgb(255, 200, 0);
    }
}

.prod-img {
    height: 230px;

}
</style>
