<script>

export default {
    data: () => ({ searchTerm: '' }),
    props: {
        placeholder: String,
        submitLabel: String,
    },
    emits: ['term-change', 'search-submit']
};

</script>

<template>
    <form @submit.prevent="$emit('search-submit')">
        <div class="d-flex gap-3">
            <input type="text" class="form-control" id="makeSearch" :placeholder="placeholder || 'Search...'"
                v-model.trim="searchTerm" @keyup="$emit('term-change', searchTerm)">
            <button type="submit" class="btn btn-danger">Search</button>
        </div>
    </form>
</template>

<style lang="scss" scoped></style>
