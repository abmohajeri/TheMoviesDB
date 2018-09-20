<template>
    <ul>
        <li v-for="movie in movies">
            <Movie :movie="movie" />
        </li>
    </ul>
</template>

<script>
    import Movie from './Movie.vue'

    export default {
        name: "movies-list",
        components: {
            Movie
        },
        data () {
            return {
                movies: []
            }
        },
        created: function() {
            this.fetchdata();
        },
        methods: {
            fetchdata: async function() {
                try {
                    const res = await fetch(
                        'https://api.themoviedb.org/3/discover/movie?sort_by=popularity.desc&api_key=acf68088c61b156440335b631f66e5d9'
                    );
                    const movies = await res.json();
                    this.movies = movies.results;
                } catch(e) {
                    console.log(e);
                }
            }
        }
    }
</script>

<style scoped>
    ul {
        display: grid;
        list-style: none;
        padding: 1rem;
        margin: 0;
        grid-row-gap: 1rem;
        grid-template-columns: repeat(6, 1fr);
    }
</style>