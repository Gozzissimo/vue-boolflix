<template>
    <header>
        <input @keyup.enter="getSearch" v-model="searchedText" type="text">
        <button @click="getSearch">
            Cerca Film o Serie Tv
        </button>
    </header>
</template>

<script>
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

</style>