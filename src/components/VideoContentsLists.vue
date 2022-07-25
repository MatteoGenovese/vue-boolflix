<template>
    <div>

        
        <div v-if="movies.length!=0">
            <h2>Movies</h2>
            <div class="list-of-movies" >
                <Content v-for="movie in movies" :key="movie.id" :content="movie" :isMovie="true" :isEmpty="false"/>
            </div>
        </div>
        
        <div v-if="tvSeries.length!=0">
            <h2>Tv Series</h2>
            <div class="list-of-series" >
                <Content v-for="tvSerie in tvSeries" :key="tvSerie.id" :content="tvSerie" :isMovie="false" :isEmpty="false" />
            </div>
        </div>
        <div v-if="tvSeries.length==0 && movies.length==0">
            <div class="no-results" >
                Non hai effettuato la ricerca oppure la tua ricerca non ha prodotto risultati.
            </div>
        </div>

    </div>

</template>

<script>

import Content from './Content.vue';

export default {
    name: 'VideoContentsLists',
    props: {
        movies: {
            type: Array,
            required: true,
        },
        tvSeries: {
            type: Array,
            required: true,
        },
    },
    components: {
    // Movie,
    // Serie,
    Content
}
}
</script>

<style scoped lang="scss">

.list-of-movies,
.list-of-series{
    display : flex;
    flex-wrap: wrap;
    row-gap: 20px;
}

.no-results, h2{
    color: white;
    font-size: 2rem;
}

</style>