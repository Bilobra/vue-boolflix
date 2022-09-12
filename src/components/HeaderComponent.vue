<template>
    <header>
        <div class="logo-wrapper">
            <a href="#" class="logo">
                BOOLFLIX
            </a>
        </div>

        <div class="search-wrapper">
            <input class="search-bar" type="text" placeholder="Cerca..." v-model="searchInput">

            <!-- <button @click="getchMovies">
                Cerca
            </button> -->

            <input class="search-button" type="button" value="cerca" @click="getchMovies">

        </div>


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
            series: [],
            api_key: '26178dc21df4958017d42bad7afceca4',
            // query : '',
            BASE_URI: 'https://api.themoviedb.org/3',


        }
    },

    methods: {
        getchMovies() {
            axios
                .get(`${this.BASE_URI}/search/movie?api_key=${this.api_key}&query=${this.searchInput}`)
                // .get(`${this.BASE_URI}/search/tv?api_key=${this.api_key}&query=${this.searchInput}`)

                .then((res) => {
                    this.movies = res.data.results;
                    // this.$emit('searchInput', this.searchInput);
                    this.$emit('movies', this.movies);
                    // this.$emit('series', this.series);

                })


            axios
                // .get(`${this.BASE_URI}/search/movie?api_key=${this.api_key}&query=${this.searchInput}`)
                .get(`${this.BASE_URI}/search/tv?api_key=${this.api_key}&query=${this.searchInput}`)

                .then((res) => {
                    this.series = res.data.results;
                    // this.$emit('searchInput', this.searchInput);
                    // this.$emit('movies', this.movies);
                    this.$emit('series', this.series);

                })
        }
    },

    // created(){
    //     this.getchMovies()
    // },
}
</script>


<style lang="scss" scoped>
header {
    background-color: #000;
    padding: 1rem;
    display: flex;
    justify-content: space-between;
    align-items: center;

    .logo-wrapper {
        .logo {
            font-size: 2rem;
            color: red;
            text-decoration: none;
        }
    }

    .search-wrapper{
        .search-bar, .search-button{
            padding: 0.5rem 0.2rem;
            margin: 0 0.5rem;
            font-size: 1rem;
        }
    }
}
</style>