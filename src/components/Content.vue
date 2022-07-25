<template>
    <div>
        <transition name="rotate">
            <div class="content" @mouseover="showFront = false" @mouseleave="showFront = true">
                <div class="front d-flex align-items-center justify-content-center" v-if="showFront">
                    <div v-if="isMovie">
                        <img v-if="content.poster_path != null" class="w-100"
                            :src="basicImageUrl + poster_sizes[3] + content.poster_path" :alt="content.poster_path">
                        <img v-else :src="basicImageUrl + poster_sizes[3] + content.poster_path"
                            class="d-flex justify-content-center" :alt="content.title">
                    </div>
                    <div v-else>
                        <img v-if="content.poster_path != null" class="w-100"
                            :src="basicImageUrl + poster_sizes[3] + content.poster_path" :alt="content.poster_path">
                        <img v-else :src="basicImageUrl + poster_sizes[3] + content.poster_path"
                            class="d-flex justify-content-center" :alt="content.name">
                    </div>

                </div>
                <div class="back" v-else>
                    <ul>
                        <li v-if="isMovie">
                            
                            <span>Titolo: {{ content.title }}</span> 
                            <span>Titolo Originale: {{ content.original_title }}</span> 
                        </li>
                        <li v-else>
                            <span>Titolo: {{ content.name }}</span> 
                            <span>Titolo Originale: {{ content.original_name }}</span> 
                        </li>
                        <li>Lingua:
                            <span v-if="content.original_language === 'en'">
                                <country-flag
                                  :country='"gb"'
                                  size='small' />
                            </span>
                            <span v-if="content.original_language === 'ja'">
                                <country-flag
                                  :country='"jp"'
                                  size='small' />
                            </span>
                            <span v-else>
                                <country-flag
                                  :country='content.original_language'
                                  size='small' />
                            </span>
                            <span> {{ content.original_language.toUpperCase() }}</span>
                        </li>
                        <li>
                            <star-rating
                            :increment="1"
                            :max-rating="5"
                            inactive-color="#999999"
                            active-color="#F8D36B"
                            :star-size="20"
                            :read-only="true"
                            :rating="content.vote_average / 2">
                            </star-rating>
                        </li>
                        <li v-if="content.overview!=''">Descrizione: {{ content.overview }}</li> 

                    </ul>
                </div>
            </div>

        </transition>

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
            // https://www.themoviedb.org/talk/53c11d4ec3a3684cf4006400 available size of image
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
            showBack: false,
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

.content {
    width: $card_width;
    height: $card_height;
        overflow:hidden;

    display: flex;
    flex-direction: column;
    justify-content: center;
    background-color: #000000;
    color: white;

    &:hover {
        cursor: pointer;
    }
    .back{
        overflow:auto;
    }


    ul {
        list-style: none;
        li{
            padding-top: 10px;
            span{
                display: inline-block;
                padding-top: 10px;
            }
        }
    }

    img {
        object-fit: contain;
        scale: 110%;

    }
}

.rotate-enter-active {
    animation: finished 2.5s reverse;
}

.rotate-leave-active {
    animation: finished 2.5s;
}

@keyframes finished {
    0% {
        opacity: 1;
        top: 0;
    }

    50% {
        opacity: 1;
        top: 0;
    }

    60% {
        opacity: 1;
    }

    100% {
        opacity: 0;
        top: -100vh;
    }
}
</style>