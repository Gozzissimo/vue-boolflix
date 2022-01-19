<template>
    <header>
        <input v-model="movieName" type="text">
        <button @click="movieSearch">
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
                movieLanguage: '',
                movieName: '',
                filteredMovies: null
            }
        },

        methods: {

            movieSearch() {
                axios
                    .get(this.query, {
                        params: {
                            api_key: this.apiKey,
                            language: this.movieLanguage,
                            query: this.movieName
                        }
                    })
                    .then((response) => {
                        // console.log(response);
                        // console.log(response.data.results);
                        // console.log(this.filteredMovies);
                        this.filteredMovies = response.data.results;
                        // console.log(this.filteredMovies);
                        // console.log(this.movieName);
                        this.$emit('movieSearch', this.filteredMovies)
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