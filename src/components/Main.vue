<template>
    <main>
        <ul>
            <FilmCard 
                v-for="(movie, index) in movies"
                :key="index"
                :movieTitle="movie.title"
                :originalTitle="movie.original_title"
                :language="movie.original_language"
                :rating="movie.vote_average"
            />
        </ul>
    </main>
</template>

<script>
import FilmCard from "./FilmCard.vue";

export default {
    name: "Main",
    components: {
        FilmCard,
    },

    props: {
        movies: {
            type: Array,
        },
    },
}
</script>

<style lang="less" scoped>

</style>