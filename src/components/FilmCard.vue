<template>
    <li>
        <h1 v-if="movieTitle">Movie</h1>
        <h1 v-else>Tv Series</h1>
        <div class="img">
            <img
            :src="(poster == null) ? require('../assets/img/Image-Not-Available.png') : 'https://image.tmdb.org/t/p/w342' + poster"
            :alt="movieTitle || tvShowName">
        </div>
        <div>{{ movieTitle || tvShowName}}</div>
        <div>{{ originalTitle || tvShowOriginalName}}</div>
        <LangFlag :iso="language" />
        <i
            v-for="n in 5"
            :key="n"
            :class="(n <= ((Math.round(rating)) / 2)) ? 'fas fa-star' : 'far fa-star'"
        />
    </li>
</template>

<script>
import LangFlag from 'vue-lang-code-flags';
import '@fortawesome/fontawesome-free/css/all.css';

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
        poster: {
            type: String,
        },
    },
}
</script>

<style lang="scss" scoped>
    li {
        margin: 1em;
        .img {
            width: 200px;
            height: 300px;
            img {
                width: 100%;
            }
        }
    }
</style>
