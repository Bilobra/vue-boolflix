<template>
    <main>
        <h1>film</h1>
        <!-- FILM -->
        <ul>
            <li v-for="(film,i) in movies" :key="i">
                <div>{{film.title}}</div>
                <ul>
                    <li>
                        <div>{{film.original_title}}</div>
                    </li>
                    <li>
                        <div>{{film.original_language}}</div>
                    </li>
                    <li>
                        <div>{{film.vote_average}}</div>
                    </li>
                </ul>
            </li>
        </ul>
        <!-- SERIE TV -->
        <h1>serie tv</h1>
        <ul>
            <li v-for="(stv,i) in series" :key="i">
                <div>{{stv.name}}</div>
                <ul>
                    <li>
                        <div>{{stv.originale_name}}</div>
                    </li>
                    <li>
                        <div>{{stv.original_language}}</div>
                    </li>
                    <li>
                        <div>{{stv.vote_average}}</div>
                    </li>
                </ul>
            </li>
        </ul>
    </main>
</template>

<script>
export default {
    name: 'MainComponent',
    props: {
        // searchInput: String,
        movies: Array,
        series : Array,
    }
}
</script>

<style lang="scss" scoped>

</style>