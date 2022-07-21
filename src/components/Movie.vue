<template>
    <div>
        Titolo: {{movie.title}}
        Titolo Originale: {{movie.original_title}}
        <country-flag :country='movie.original_language' size='normal'/>
        Voto: {{movie.vote_average}} 
    </div>

</template>

<script>

import CountryFlag from 'vue-country-flag';

export default {
    // https://www.npmjs.com/package/vue-country-flag



    props: {
        movie: {
            type: Object,
            required: true,
        },
    },
    components:{
        CountryFlag
    }

}
</script>

<style>
</style>