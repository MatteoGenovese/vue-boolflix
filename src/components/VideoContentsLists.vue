<template>
    <div>

        
        <div class="list-of-movies" v-if="movies.length!=0">
            <h2>Movies</h2>
            <Content v-for="movie in movies" :key="movie.id" :content="movie" :isMovie="true"/>
        </div>
        
        <div class="list-of-series" v-if="tvSeries.length!=0">
            <h2>Tv Series</h2>
            <Content v-for="tvSerie in tvSeries" :key="tvSerie.id" :content="tvSerie" :isMovie="false" />
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
    justify-content: space-between;
    row-gap: 20px;
}

</style>