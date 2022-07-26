<template>
    <div>

        <div class="flip-card">
            <div class="flip-card-inner">
                <div class="flip-card-front">
                    <!-- case: FILM -->
                    <div v-if="isMovie">
                        <!-- case: path is null -->
                        <img v-if="content.poster_path != null" class="w-100"
                            :src="basicImageUrl + poster_sizes[3] + content.poster_path" :alt="content.poster_path">
                        <!-- case: path is not null and the poster is visible-->
                        <img v-else :src="basicImageUrl + poster_sizes[3] + content.poster_path"
                            class="d-flex justify-content-center" :alt="content.title">
                    </div>
                    <!-- case: TV SERIE -->
                    <div v-else>
                        <!-- case: path is null -->
                        <img v-if="content.poster_path != null" class="w-100"
                            :src="basicImageUrl + poster_sizes[3] + content.poster_path" :alt="content.poster_path">
                        <!-- case: path is not null and the poster is visible-->
                        <img v-else :src="basicImageUrl + poster_sizes[3] + content.poster_path"
                            class="d-flex justify-content-center" :alt="content.name">
                    </div>
                </div>
                <div class="flip-card-back">
                    <ul>
                        <!-- case: FILM -->
                        <li v-if="isMovie">
                            Titolo: {{ content.title }}
                        </li>
                        <li v-if="isMovie && content.original_title != content.title">
                            Titolo Originale: {{ content.original_title }}
                        </li>
                        <!-- case: TV SERIE -->
                        <li v-if="!isMovie">
                            Titolo: {{ content.name }}
                        </li>
                        <li v-if="!isMovie && content.original_name != content.name">
                            Titolo Originale: {{ content.original_name }}
                        </li>
                        <!-- case: information in common -->
                        <li>Lingua:
                            <span v-if="content.original_language === 'en'">
                                <country-flag :country='"gb"' size='small' />
                            </span>
                            <span v-if="content.original_language === 'ja'">
                                <country-flag :country='"jp"' size='small' />
                            </span>
                            <span v-else>
                                <country-flag :country='content.original_language' size='small' />
                            </span>
                            <span> {{ content.original_language.toUpperCase() }}</span>
                        </li>
                        <li>
                            <star-rating :increment="1" :max-rating="5" inactive-color="#999999" active-color="#F8D36B"
                                :star-size="20" :read-only="true" :rating="content.vote_average / 2">
                            </star-rating>
                        </li>
                        <li v-if="content.overview != ''">Descrizione: {{ content.overview }}</li>
                    </ul>
                </div>
            </div>
        </div>





    </div>
</template>

<script>
// https://www.npmjs.com/package/vue-country-flag country flag documentation
import CountryFlag from 'vue-country-flag';
// https://www.npmjs.com/package/vue-star-rating star rating documentation
import StarRating from 'vue-star-rating'
export default {
    name: 'Content',
    props: {
        content: {
            type: Object,
            required: true,
        },
        isMovie: {
            type: Boolean,
            required: true,
        },
        isEmpty: {
            type: Boolean,
            required: true,
        }
    },
    components: {
        CountryFlag,
        StarRating
    },
    data: function () {
        return {
            basicImageUrl: 'https://image.tmdb.org/t/p/',
            // https://www.themoviedb.org/talk/53c11d4ec3a3684cf4006400 available sizes of images
            poster_sizes: [
                "w92",
                "w154",
                "w185",
                "w342",
                "w500",
                "w780",
                "original"
            ],
            showFront: true,
        }
    },
    methods: {
        whereIAm() {
            console.log(this.isMovie);
        }
    }
}
</script>

<style scoped lang="scss" >
$card_width: calc((100vw / 5) - 7px);
$card_height: calc($card_width * 1.5);

// https://www.w3schools.com/howto/howto_css_flip_card.asp card flip documentation

/* The flip card container - set the width and height to whatever you want. We have added the border property to demonstrate that the flip itself goes out of the box on hover (remove perspective if you don't want the 3D effect */
.flip-card {
    background-color: transparent;
    width: $card_width;
    height: $card_height;
    perspective: 1000px;
    /* Remove this if you don't want the 3D effect */
}

/* This container is needed to position the front and back side */
.flip-card-inner {
    position: relative;
    width: 100%;
    height: 100%;
    transition: transform 0.8s;
    transform-style: preserve-3d;
}

/* Do an horizontal flip when you move the mouse over the flip box container */
.flip-card:hover .flip-card-inner {
    transform: rotateY(180deg);
}

/* Position the front and back side */
.flip-card-front,
.flip-card-back {
    position: absolute;
    width: 100%;
    height: 100%;
    -webkit-backface-visibility: hidden;
    /* Safari */
    backface-visibility: hidden;
}

.flip-card-front{
    color: #CC2E25;
    background: #000;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 2rem;
    text-align: center;
}

/* Style the back side */
.flip-card-back {
    background-color: #000;
    color: white;
    transform: rotateY(180deg);
    display: flex;
    align-items: flex-start;
    overflow: auto;

    ul {
        display: flex;
        flex-direction: column;
        justify-content: flex-start;

        li {
            display: flex;
            flex-wrap: wrap;
            justify-content: flex-start;
            padding-top: 10px;
        }
    }
}
</style>