<template>
    <li 
        @mouseover="upHere = true" 
        @mouseleave="upHere = false" 
        class="card">
            <!-- <h1 v-if="movieTitle">Movie</h1>
            <h1 v-else>Tv Series</h1> -->
            <div 
                v-if="upHere"
                class="info text-center">
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
    @import "../assets/scss/partials/_variables.scss";

    .card{
        height: 340px;
        width: 200px;
        margin: 10px;
        overflow-wrap: break-word;
        overflow: hidden;
        color: $whiteFontColor;
        border-radius: 10px;
        & :hover {
            cursor: pointer;
        }
        .poster {
            img {
                object-fit: cover;
                height: 340px;
                width: 200px;
            }
        }
        .info {
            padding: 1em 0;
            span:first-child {
                font-weight: bold;
            }
            i {
                color: #b70a13;
            }
            .overview {
                overflow-y: auto;
                height: 180px;
                
            }
            .overview::-webkit-scrollbar {
            width: 12px;               /* width of the entire scrollbar */
            }

            .overview::-webkit-scrollbar-track {
            background: $darkBgColor;        /* color of the tracking area */
            }

            .overview::-webkit-scrollbar-thumb {
            background-color: $redFontColor;    /* color of the scroll thumb */
            border-radius: 20px;       /* roundness of the scroll thumb */
            border: 3px solid $darkBgColor;  /* creates padding around scroll thumb */
            }
        }
    }
</style>
