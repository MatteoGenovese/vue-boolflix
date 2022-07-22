<template>
    <div>
        <transition name="rotate">
            <div class="movie" @mouseover="showFront=false" @mouseleave="showFront=true">
                <div class="front d-flex align-items-center justify-content-center" v-if="showFront">
                    <img v-if="movie.poster_path != null" class="w-100" :src="basicImageUrl + poster_sizes[3] + movie.poster_path"
                        :alt="movie.poster_path">
                    <img v-else :src="basicImageUrl + poster_sizes[3] + movie.poster_path"
                        class="d-flex justify-content-center" :alt="movie.title">
                </div>
                <div class="back" v-else>
                    <ul>
                        <li>Titolo: {{ movie.title }}</li>
                        <li>Titolo Originale: {{ movie.original_title }}</li>
                        <li>Lingua:<country-flag :country='movie.original_language' size='normal' />
                            {{movie.original_language}}
                        </li>
                        <li>
                            <star-rating :increment="1" :max-rating="5" inactive-color="#999999" active-color="#F8D36B"
                                :star-size="20" :read-only="true" :rating="movie.vote_average / 2">
                            </star-rating>
                        </li>
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
    name: 'Movie',
    props: {
        movie: {
            type: Object,
            required: true,
        },
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
            showFront:true,
            showBack:false,

        }
    },

}
</script>

<style scoped lang="scss" >

$card_width:calc((100vw / 5) - 10px);
$card_height: calc( $card_width * 1.5 );

.movie,
.tv-serie {
    width: $card_width;
    height: $card_height;
    overflow: hidden;
    display: flex;
    flex-direction: column;
    justify-content: center;
    

    ul {
        list-style: none;
    }

    img {
        object-fit: contain;

    }
}

.rotate-enter-active {
    animation: finished 2.5s reverse;
  }
  .rotate-leave-active {
    animation: finished 2.5s;
  }
  @keyframes finished {
    0% { opacity: 1; top: 0;}
    50% { opacity: 1; top: 0;}
    60% { opacity: 1; }
    100% { opacity: 0; top: -100vh;}
  }
</style>