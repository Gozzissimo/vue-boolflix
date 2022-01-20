<template>
    <li>
        <h1>{{ movieTitle }}</h1>
        <h2>{{ originalTitle }}</h2>
        <lang-flag :iso="language" />
        <h4>{{ rating }}</h4>
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
        language: {
            type: String,
        },
        rating: {
            type: Number,
        },
    },
}
</script>

<style>

</style>