<template>
    <li 
        @mouseover="upHere = true" 
        @mouseleave="upHere = false" 
        class="card">
            <!-- <h1 v-if="movieTitle">Movie</h1>
            <h1 v-else>Tv Series</h1> -->
            <div 
                v-if="upHere"
                class="info">
                    <div>
                        <span>Titolo: </span>
                        <span>{{ movieTitle || tvShowName}}</span>
                    </div>
                    <div>
                        <span>Titolo Originale: </span>
                        <span>{{ originalTitle || tvShowOriginalName}}</span>
                    </div>
                    <div>
                        <span>Lingua: </span>
                        <LangFlag :iso="language" />
                    </div>
                    <div>
                        <span>Voto: </span>
                        <i
                            v-for="star in 5"
                            :key="star"
                            :class="(star <= ((Math.round(rating)) / 2)) ? 'fas fa-star' : 'far fa-star'"
                        />
                    </div>
                    <div class="overview">
                        <span>Overview: </span>
                        <span> {{ overview }} </span>
                    </div>
            </div>
            <div v-else class="poster">
                <img
                :src="(poster == null) ? require('../assets/img/Image-Not-Available.png') : 'https://image.tmdb.org/t/p/w342' + poster"
                :alt="movieTitle || tvShowName">
            </div>
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
        overview: {
            type: String,
        },
    },

    data() {
        return {
            upHere : false
        }
    }
}
</script>

<style lang="scss" scoped>
    .card{
        width: 250px;
        height: 300px;
        border: 2px solid black;
        overflow-wrap: break-word;
        overflow: hidden;
        .poster {
            width: 250px;
            height: 350px;
            img {
                width: 100%;
            }
        }
    }
</style>
