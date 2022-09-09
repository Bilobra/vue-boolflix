<template>
    <header>
        <input type="text" placeholder="Cerca..." v-model="searchInput">

        <button @click="getchMovies">
            Cerca
        </button>


    </header>
</template>

<script>

// importo axios per la chiamata

import axios from 'axios'

export default {
    name: 'HeaderComponent',

    data() {
        return {
            searchInput: '',
            movies: [],
            api_key: '26178dc21df4958017d42bad7afceca4',
            // query : '',
            BASE_URI: 'https://api.themoviedb.org/3',
        }
    },

    methods: {
        getchMovies() {
            axios
                .get(`${this.BASE_URI}/search/movie?api_key=${this.api_key}&query=${this.searchInput}`)
                .then((res) => {
                    this.movies = res.data.results;
                    this.$emit('searchInput', this.searchInput);
                    this.$emit('movies', this.movies);
                })
        }
    },

    // created(){
    //     this.getchMovies()
    // },
}
</script>


<style lang="scss" scoped>

</style>