<template>
  <div id="app">
    <div v-for="(mov,index) in filmes" :key="index">
     <h1> {{index + 1}} {{mov.original_title}} </h1>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  name: 'App',
  data(){
    return{
      filmes: []
    }
  },
  created: function(){
    axios.get("https://api.themoviedb.org/3/list/50941077760ee35e1500000c?api_key=b02c26e7cdf8332f6747485120b222dc&language=pt-BR").then(res => {
      console.log("PEGOU A LISTA DE FILMES");
      this.filmes = res.data.items;
    })
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
