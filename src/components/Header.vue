<template>
<header>
  <input type="text" v-model="inputText">
  <button @click="$emit('search', inputText)">Invio</button>
</header>
</template>

<script>
export default {
  name: 'Header',
  data: function () {
    return {
      inputText:"",
    }
  },
  props: {
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>
