<template>
        <router-link :to="moviepath">
            <img :src="posterImage" :alt="movie.title">
        </router-link>
</template>

<script>
    const POSTER_PATH = "http://image.tmdb.org/t/p/w154";

    export default {
        name: "movie",
        props: ['movie'],
        computed : {
            posterImage: function () {
                return `${POSTER_PATH}/${this.movie.poster_path}`;
            },
            moviepath: function () {
                return `/movie/${this.movie.id}`;
            }
        }
    }
</script>

<style scoped>
    img {
        box-shadow: 0 0 35px grey;
    }
</style>