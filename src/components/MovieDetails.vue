<template>
    <transition name="fade">
        <div class="moviedetails" :style="styles">
            <div class="movietxt">
                <h1> {{ movie.title }} </h1>
                <h3> {{ movie.release_date }} </h3>
                <p>
                    {{ movie.overview }}
                </p>
            </div>
        </div>
    </transition>
</template>

<script>
    const BACKDROP_PATH = "http://image.tmdb.org/t/p/w1280";

    export default {
        name: "movie-details",
        data () {
            return {
                movie: {}
            }
        },
        created: function() {
            this.fetchdata();
        },
        computed: {
            styles() {
                return {
                    'background-image': `url(${BACKDROP_PATH}/${this.movie.backdrop_path})`,
                    'background-repeat': 'no-repeat',
                    'background-size': 'cover'
                };
            }
        },
        methods: {
            fetchdata: async function() {
                try {
                    const res = await fetch(
                        `https://api.themoviedb.org/3/movie/${this.$route.params.id}?api_key=acf68088c61b156440335b631f66e5d9`
                    );
                    const movie = await res.json();
                    this.movie = movie;
                } catch(e) {
                    console.log(e);
                }
            }
        }
    }
</script>

<style scoped>
    .moviedetails {
        position: relative;
        padding-top: 70vh;
    }
    .movietxt {
        background: white;
        color: black;
        padding: 2rem 10%;
    }
</style>