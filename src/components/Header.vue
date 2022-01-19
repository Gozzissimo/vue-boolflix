<template>
    <header>
        <input v-model="movieName" type="text">
        <button @click="$emit('movieSearch', filteredMovies)">
            Cerca Film
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
                query: 'https://api.themoviedb.org/3/search/movie',
                apiKey: '67eae03458a1925dc99578a8eaf2f7c6',
                movieLanguage: 'en-US',
                movieName: '',
                filteredMovies: null
            }
        },

        methods: {

            movieSearch() {
                axios
                    .get('https://api.themoviedb.org/3/search/movie', {
                        params: {
                            api_key: this.apiKey,
                            language: this.movieLanguage,
                            query: this.movieName
                        }
                    })
                    .then((response) => {
                        console.log(response);
                        console.log(response.data.results);
                        console.log(this.filteredMovies);
                        this.filteredMovies = response.data.results;

                        this.$emit('filteredMovies', this.filteredMovies);
                        // console.log(this.filteredMovies);
                    })
                    .catch(function (error) {
                        console.log(error);
                    });
            }
        }
    }
</script>

<style lang="less" scoped>

</style>