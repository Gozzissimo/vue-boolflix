<template>
    <li>
        <div>{{ movieTitle }}</div>
        <div>{{ tvShowName }}</div>
        <div>{{ originalTitle }}</div>
        <div>{{ tvShowOriginalName }}</div>
        <LangFlag :iso="language" />
        <div>{{ rating }}</div>
    </li>
</template>

<script>
import LangFlag from 'vue-lang-code-flags';

export default {
    name: "FilmCard",

    components: {
        LangFlag,
    },

    props: {
        movieTitle: {
            type: String,
        },
        originalTitle: {
            type: String,
        },
        tvShowName: {
            type: String,
        },
        tvShowOriginalName: {
            type: String,
        },
        language: {
            type: String,
        },
        rating: {
            type: Number,
        },
    },
}
</script>

<style lang="scss" scoped>
    li {
        margin: 1em;
    }
</style>
