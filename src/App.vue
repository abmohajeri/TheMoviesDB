<template>
  <div id="app">
    <Header :title="title" />
    <router-view />
  </div>
</template>

<script>

import Header from './components/Header.vue'

export default {
  name: 'app',
  data() {
      return {
          title: 'Movies DataBase'
      }
  },
  components: {
    Header
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #fff;
}
.fade-enter-active, .fade-leave-active {
  transition: all 0.3s ease;
}
.fade-enter, .fade-leave-to {
  opacity: 0;
  transform: scale(0);
}
</style>
