<template>
    <ul>
        <li v-for="movie in movies">
            {{ movie.title }}
        </li>
    </ul>
</template>

<script>
    export default {
        name: "movies-list",
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

</style>