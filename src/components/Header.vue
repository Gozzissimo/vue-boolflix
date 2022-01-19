<template>
    <header>
        <!-- <input v-model="movieName" type="text" name="search" id="search">
        <button @click="searchMovie">Cerca</button> -->
    </header>
</template>

<script>
import axios from 'axios';

export default {
    name: "Header",
    
    data() {
        // apiKey = '67eae03458a1925dc99578a8eaf2f7c6',
        // movieLanguage = 'en-US'
        // movieName = 'mad max'
    },

    created() {
        axios.get('https://api.themoviedb.org/3/search/movie?api_key=', {
            params: {
                api_key: '67eae03458a1925dc99578a8eaf2f7c6',
                // language: 'en-US',
                query: 'max'
            }
        })
        .then(function (response) {
        console.log(response);
        })
        .catch(function (error) {
        console.log(error);
        });
    }
}
</script>

<style lang="less" scoped>

</style>