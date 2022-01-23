<template>
    <header class="flex">
        <img src="../assets/img/logo.png" alt="fantaflix logo">
        <div class="box">
            <input
                @keyup.enter="getSearch" 
                v-model="searchedText" 
                type="text" 
                placeholder="Cerca Film e Serie TV">
            <i @click="getSearch" class="fas fa-search"></i>
        </div>
    </header>
</template>

<script>
    import '@fortawesome/fontawesome-free/css/all.css';
    import axios from 'axios';

    export default {
        name: "Header",
        props: {
            genres: {
                type: Array,
            },
    },
        
        data() {
            return {
                movieQuery: 'https://api.themoviedb.org/3/search/movie',
                tvQuery: 'https://api.themoviedb.org/3/search/tv',
                apiKey: '67eae03458a1925dc99578a8eaf2f7c6',
                movieLanguage: '',
                searchedText: '',
                filteredMovies: [],
                filteredTvShows: [],
                moviesAndTvShows: []
            }
        },

        methods: {

            getSearch() {
                this.movieSearch();
                this.tvShowsSearch();
                // console.log(this.filteredMovies);
                // console.log(this.filteredTvShows);
                setTimeout(() => {
                    this.getMerged();
                    this.$emit('mergedList', this.moviesAndTvShows);
                }, 500);
            },

            getMerged() {
                this.moviesAndTvShows = [...this.filteredMovies, ...this.filteredTvShows];
                console.log(this.filteredMovies);
                console.log(this.filteredTvShows);
                // console.log(this.moviesAndTvShows);
            },

            movieSearch() {
                axios
                    .get(this.movieQuery, {
                        params: {
                            api_key: this.apiKey,
                            language: this.movieLanguage,
                            query: this.searchedText
                        }
                    })
                    .then((response) => {
                        // console.log(response);
                        // console.log(response.data.results);
                        // console.log(this.filteredMovies);
                        this.filteredMovies = response.data.results;
                        // console.log(this.filteredMovies);
                        // console.log(this.searchedText);
                        // this.$emit('movieSearch', this.filteredMovies)
                    })
                    .catch(function (error) {
                        console.log(error);
                    });
            },


            tvShowsSearch() {
                axios
                    .get(this.tvQuery, {
                        params: {
                            api_key: this.apiKey,
                            language: this.movieLanguage,
                            query: this.searchedText
                        }
                    })
                    .then((response) => {
                        // console.log(response);
                        // console.log(response.data.results);
                        // console.log(this.tvShowsSearch);
                        this.filteredTvShows = response.data.results;
                        // console.log(this.tvShowsSearch);
                        // console.log(this.searchedText);
                        // this.$emit('tvShowsSearch', this.filteredTvShows)
                    })
                    .catch(function (error) {
                        console.log(error);
                    });
            }
        }
    }
</script>
    
<style lang="scss" scoped>
    @import "../assets/scss/partials/_variables.scss";
    
    

    header {
        height: 100px;
        justify-content: space-between;
        align-items: center;
        padding: 1em;
        position: relative;
        input {
            padding: 10px;
            width: 80px;
            height: 70px;
            background: none;
            border: 4px solid $redFontColor;
            border-radius: 50px;
            font-size: 1.2em;
            color: $whiteFontColor;
            outline: none;
            transition: .5s;
        }
        .box:hover input {
            width: 350px;
            background: $lightBgColor;
            border-radius: 10px;
        }
        i {
            font-size: 26px;
            color: $redFontColor;
            margin-left: 10px;
            cursor: pointer;
        }
    }
</style>