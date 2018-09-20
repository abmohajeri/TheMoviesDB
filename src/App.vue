<template>
  <div id="app" v-if="status === 'ready'">
    <Header :title="title" />
    <MoviesList />
  </div>
  <div v-else-if="status === 'loading'">
    Loading
  </div>
  <div v-else>
    Error
  </div>
</template>

<script>

import Header from './components/Header.vue'
import MoviesList from './components/MoviesList.vue'

export default {
  name: 'app',
  data() {
      return {
          hello: '',
          title: 'MoviesDB',
          status: 'ready'
      }
  },
  components: {
    Header,
    MoviesList
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
