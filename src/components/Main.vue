<template>
    <main>
        <ul class="flex">
            <FilmCard 
                v-for="(movie, index) in movies"
                :key="index"
                :movieTitle="movie.title"
                :tvShowName="movie.name"
                :originalTitle="movie.original_title"
                :tvShowOriginalName="movie.original_name"
                :language="movie.original_language"
                :rating="movie.vote_average"
                :poster="movie.poster_path"
                :overview="movie.overview"
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

<style lang="scss" scoped>
    .flex{
        display: flex;
        flex-wrap: wrap;
        list-style: none;
    }
</style>