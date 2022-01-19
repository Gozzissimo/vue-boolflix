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
        
        data() {
            return {
                apiKey: '67eae03458a1925dc99578a8eaf2f7c6',
                movieLanguage: 'en-US',
                movieName: '',
                movieList: null
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
                        // console.log(response);
                        // console.log(response.data.results);
                        // console.log(this.movieList);
                        this.movieList = response.data.results;
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