<template>
  <header>
    <div class="logo">
      <img src="../assets/netflix-logo.png" alt="">
    </div>
    <nav>
      <ul>
        <li>Home</li>
        <li>Serie TV</li>
        <li>Film</li>
        <li>Originali</li>
        <li>Aggiunti di recente</li>
        <li>La mia lista</li>
      </ul>

    </nav>
    <div class="search-bar">
      <input type="text" v-model="inputText" @keyup.enter="$emit('search', inputText)">
      <button @click="$emit('search', inputText)">Invio</button>
    </div>

  </header>
</template>

<script>
export default {
  name: 'Header',
  data: function () {
    return {
      inputText: "",
    }
  },
  props: {
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

header {
  height: 70px;
  background-color: #000;
  color: white;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding-left: 10px;
  padding-right: 10px;
  .logo{
    height: 60px;
    img{
      height: 100%;
      object-fit: contain;
    }
  }
  nav{
    ul{
      display: flex;
      li{
        list-style: none;
        padding: 10px;
      }
      }
    
  }
  .search-bar{
    flex-grow: 1;
    display: flex;
    justify-content: flex-end;
  }
}
</style>
