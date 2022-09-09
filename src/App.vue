<template>
  <div id="app">
    <HeaderComponent @searchInput="getInputFromHeader" @movies="getMovies" />

    <MainComponent  :movies="headerMovies" />

  </div>
</template>

<script>
import HeaderComponent from './components/HeaderComponent.vue';
import MainComponent from './components/MainComponent.vue';

export default {
  name: 'App',
  components: {
    HeaderComponent,
    MainComponent,
  },
  data() {
    return {
      headerSearchInput: '',
      headerMovies: [],
    }
  },
  methods: {
    getInputFromHeader(input) {
      this.headerSearchInput = input
    },

    getMovies(headerMovies) {
      this.headerMovies = headerMovies
    }
  }
}
</script>

<style lang="scss">

</style>
