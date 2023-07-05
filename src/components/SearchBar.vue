<script>

export default {
    data: () => ({ searchTerm: '' }),
    props: {
        placeholder: String,
    },
    emits: ['term-change', 'search-submit']
};

</script>

<template>
    <form>
        <div class="mb-3">
            <input type="text" class="form-control" id="makeSearch" :placeholder="placeholder || 'Search...'"
                v-model.trim="searchTerm" @keyup="$emit('term-change', searchTerm)">
            <button type="submit" class="btn btn-primary" @click="$emit('search-submit')">Submit</button>
        </div>
    </form>
</template>

<style></style>
