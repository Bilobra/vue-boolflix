<template>
    <main>

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

    </main>
</template>

<script>
export default {
    name: 'MainComponent',
    props: {
        // searchInput: String,
        movies: Array,
    }
}
</script>

<style lang="scss" scoped>

</style>