<template>
    <div>
        Titolo: {{movie.title}}
        Titolo Originale: {{movie.original_title}}
        Lingua: {{movie.original_language}}
        Voto: {{movie.vote_average}} 
    </div>

</template>

<script>

export default {
    props: {
        movie: {
            type: Object,
            required: true,
        },
    },

}
</script>

<style>
</style>