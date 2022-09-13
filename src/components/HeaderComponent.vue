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
    background-color: rgba(21, 20, 20, 0.896);
    padding: 2rem;
    display: flex;
    justify-content: space-between;
    align-items: center;

    .logo-wrapper {
        .logo {
            font-size: 4rem;

            color: rgba(50, 3, 3, 0.776);
            text-decoration: none;
            text-shadow: -5px 9px 0px #0000002b;
            font-family: monospace;
            font-weight: 600;

            &:hover{
                transform: scale(1.3);
                color: white;
                cursor: pointer;
            }
        }
    }

    .search-wrapper {

        .search-bar,
        .search-button {
            padding: 0.7rem 1rem;
            margin: 0 0.9rem;
            font-size: 1rem;
            border-radius: 4px;
            border: none;
            background-color: rgba(50, 3, 3, 0.776);
            color: white;
            box-shadow: -3px 5px 8px #0000002b;

        }

        .search-button {
            padding: 0.7rem 1.5rem;
            transition: all 200ms;
            text-transform: uppercase;

            &:hover {
                transform: scale(1.2);
            }
        }
    }
}
</style>