<template>
    <main>
        <h1>film</h1>
        <!-- FILM -->
        <ul>
            <li v-for="(film,i) in NewMovies" :key="i">
                <div>{{film.title}}</div>
                <ul>
                    <li>
                        <img :src="film.poster" :alt="film.title">
                    </li>
                    <li>
                        <div>{{film.original_title}}</div>
                    </li>
                    <li>
                        <div>{{film.lang}}</div>
                    </li>
                    <li>
                        <div>{{film.vote}}</div>
                    </li>
                    <li>
                        <font-awesome-icon icon="fa-solid fa-star" v-for="(rating,i) in getStarVote(film.vote)"
                            :key="i" />

                        <font-awesome-icon icon="fa-regular fa-star" v-for="(rating,i) in (5 -getStarVote(film.vote))"
                            :key="i" />

                    </li>
                </ul>
            </li>
        </ul>
        <!-- SERIE TV -->
        <h1>serie tv</h1>
        <ul>
            <li v-for="(stv,i) in NewSeries" :key="i">
                <div>{{stv.name}}</div>
                <ul>
                    <li>
                        <img :src="stv.poster" :alt="stv.name">
                    </li>
                    <li>
                        <div>{{stv.original_name}}</div>
                    </li>
                    <li>
                        <div>{{stv.lang}}</div>
                    </li>
                    <li>
                        <div>{{stv.vote}}</div>
                    </li>
                    <li>
                        <font-awesome-icon icon="fa-solid fa-star" v-for="(rating,i) in getStarVote(film.vote)"
                            :key="i" />

                        <font-awesome-icon icon="fa-regular fa-star" v-for="(rating,i) in (5 -getStarVote(film.vote))"
                            :key="i" />

                    </li>
                </ul>
            </li>
        </ul>
    </main>
</template>

<script>
export default {
    name: 'MainComponent',
    data() {
        return {
            posterBaseUri: 'https://image.tmdb.org/t/p/w342',
        }

    },
    props: {
        // searchInput: String,
        movies: Array,
        series: Array,
    },
    computed: {
        NewMovies() {
            return this.movies.map((el) => {
                const newMovie = {
                    title: el.title,
                    original_title: el.original_title,
                    lang: el.original_language,
                    poster: `${this.posterBaseUri}${el.poster_path}`,
                    vote: Math.round(el.vote_average / 2),
                }
                return newMovie
            })
        },
        NewSeries() {
            return this.series.map((el) => {
                const NewSerie = {
                    name: el.name,
                    original_name: el.original_name,
                    lang: el.original_language,
                    poster: `${this.posterBaseUri}${el.poster_path}`,
                    vote: Math.round(el.vote_average / 2),
                }
                return NewSerie
            })
        }
    },
    methods: {
        getStarVote(rating) {
            if (rating <= 2) {
                return 1;
            } else if (rating > 2 && rating <= 4) {
                return 2;
            } else if (rating > 4 && rating <= 6) {
                return 3;
            } else if (rating > 6 && rating <= 8) {
                return 4;
            } else if (rating > 8 && rating <= 10) {
                return 5;
            }
        }
    },
}


</script>

<style lang="scss" scoped>

</style>