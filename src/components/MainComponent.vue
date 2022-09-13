<template>
    <main>
        <h2>film</h2>
        <!-- FILM -->
        <ul class="film-list">
            <li class="film-wrapper" v-for="(film,i) in NewMovies" :key="i">

                <ul class="p-relative">
                    <li class="img-poster">
                        <img :src="film.poster" :alt="film.title">
                    </li>
                    <li class="card-info">
                        <p><strong>Titolo: </strong> {{film.title}}</p>
                        <p><strong>Titolo Originale: </strong> {{film.original_title}}</p>
                       
                        <p>
                            <span> <strong>Lingua: </strong> {{film.lang}} </span>
                            <img  v-if="film.flag" :src="film.flag" alt="" class="img-flag">
                        </p>
                        
                        <p>
                            <strong>Voto: </strong>
                            <font-awesome-icon class="star" icon="fa-solid fa-star" v-for="n in film.vote" :key="n" />

                            <font-awesome-icon class="star" icon="fa-regular fa-star" v-for="n in (5 - film.vote)"
                                :key="n + film.vote" />
                        </p>
                        <p>{{film.overview}}</p>


                    </li>

                </ul>
            </li>
        </ul>


        <!-- SERIE TV -->
        <h2>serie tv</h2>
        <ul class="series-list">
            <li class="series-wrapper" v-for="(stv,i) in NewSeries" :key="i">
                <!-- <div>{{stv.name}}</div>
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
                        <font-awesome-icon icon="fa-solid fa-star" v-for="(rating,i) in getStarVote(stv.vote)"
                            :key="i" />

                        <font-awesome-icon icon="fa-regular fa-star" v-for="(rating,i) in (5 - getStarVote(stv.vote))"
                            :key="i" />

                    </li>
                </ul> -->
                <ul class="p-relative">
                    <li class="img-poster">
                        <img :src="stv.poster" :alt="stv.name">
                    </li>
                    <li class="card-info">
                        <p><strong>Titolo: </strong> {{stv.name}}</p>
                        <p><strong>Titolo Originale: </strong> {{stv.original_name}}</p>
                        <p>
                            <span> <strong>Lingua: </strong> {{stv.lang}} </span>
                            <img  v-if="stv.flag" :src="stv.flag" alt="" class="img-flag">
                        </p>

                        <p>
                            <strong>Voto:</strong>
                            <font-awesome-icon class="star" icon="fa-solid fa-star" v-for="n in stv.vote" :key="n" />

                            <font-awesome-icon class="star" icon="fa-regular fa-star" v-for="n in (5 - stv.vote)"
                                :key="n + stv.vote" />
                        </p>
                        <p>{{stv.overview}}</p>


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

            flags: ['it', 'en', 'fr','sh','de','ja'],
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
                    overview: el.overview,
                    flag: this.flags.includes(el.original_language) ? require(`@/assets/${el.original_language}.png`) : null
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
                    overview: el.overview,
                    flag: this.flags.includes(el.original_language) ? require(`@/assets/${el.original_language}.png`) : null


                }
                return NewSerie
            })
        },
        // getFullPath(posterPath) {
        //     if (posterPath) {
        //         return `${this.posterBaseUri}${el.poster_path}`
        //     }
        //     return `../assets/error-img.jpg`
        // },
    },
    methods: {
        // getStarVote(rating) {
        //     if (rating <= 2) {
        //         return 1;
        //     } else if (rating > 2 && rating <= 4) {
        //         return 2;
        //     } else if (rating > 4 && rating <= 6) {
        //         return 3;
        //     } else if (rating > 6 && rating <= 8) {
        //         return 4;
        //     } else if (rating > 8 && rating <= 10) {
        //         return 5;
        //     }
        // }
    },
}


</script>

<style lang="scss" scoped>
@import '../style/Films.scss';

main {
    padding: 2rem 0;
    background-color: rgb(33, 32, 32);
    

    h2 {
        font-size: 4rem;
        text-align: center;
        padding: 1rem 0;
        text-transform: uppercase;
        color: white
    }

    .film-list,
    .series-list {
        display: flex;
        flex-wrap: wrap;
        justify-content: space-around;
        max-width: 1024px;
        margin: 0 auto;
        // margin-left: 1rem;
        gap: 20px;
    }

    .film-wrapper,
    .series-wrapper {
        width: calc(100% / 4 - 20px);
    }
    .img-flag{
        width: 20px;
        height: 15px;
    }
}
</style>