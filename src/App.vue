<template>
  <div id="app">
    <HeaderComponent @searchInput="getInputFromHeader" @movies="getMovies"  @series="getSeriesTv" />

    <MainComponent  :movies="headerMovies" :series="headerSeries" />

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
      headerSeries:[],
    }
  },
  methods: {
    getInputFromHeader(input) {
      this.headerSearchInput = input
    },

    getMovies(headerMovies) {
      this.headerMovies = headerMovies
    },

    getSeriesTv(headerSeries){
      this.headerSeries = headerSeries
    }
  }
}
</script>

<style lang="scss">

</style>
