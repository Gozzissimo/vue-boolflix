<template>
    <li>
        <h1>{{ movieTitle }}</h1>
        <h2>{{ originalTitle }}</h2>
        <h3>{{ language }}</h3>
        <h4>{{ rating }}</h4>
        <country-flag country='it' size='small'/>
    </li>
</template>

<script>
import CountryFlag from "vue-country-flag";

export default {
    name: "FilmCard",

    components: {
        CountryFlag,
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