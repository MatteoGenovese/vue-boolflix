<template>
  <header>
    <div class="logo">
      BOOLFIX
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
      <input type="text" v-model="inputText" @keyup.enter="$emit('search', inputText.trim())">
      <button @click="$emit('search', inputText.trim())">Invio</button>
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
  height: 12vh;
  background-color: #000;
  color: white;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding-left: 10px;
  padding-right: 10px;
  .logo{
    height: 60px;
    color: #CC2E25;
    display: flex;
    align-items: center;
    font-size: 2rem;
    font-weight:bolder;
    img{
      height: 100%;
      object-fit: contain;
    }
  }
  nav{
      height: 100%;
      display: flex;
      align-items: center;
    ul{
      height: 100%;
      display: flex;
      align-items: center;
      margin-bottom: 0;
      li{
        height: 100%;
        display: flex;
        align-items: center;
        list-style: none;
        padding: 10px;
      }
      }
    
  }
  .search-bar{
    flex-grow: 1;
    display: flex;
    justify-content: flex-end;
    input{
      margin-right: 10px;
      }
      button{
        padding: 0px 10px;
        border-radius: 6px;
      }
  }
}
</style>
