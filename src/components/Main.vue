<template>
  <main>
    <VideoContentsLists :movies="movies" :tvSeries="tvSeries"/>
  </main>
</template>

<script>
import VideoContentsLists from './VideoContentsLists.vue';

export default {
  name: 'Main',
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
    VideoContentsLists,
  }


}
</script>

<style>
main{
  padding: 10px;
  background-color: #565456;
  height: 100%;

}

</style>