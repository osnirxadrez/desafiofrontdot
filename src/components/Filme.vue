<template>
 <div id="filme" class="card">
     <div class="card-image">
         <figure class>
             <img :src=filme.capa  alt="Placeholder image">
         </figure>
     </div>
     <div class="card-content">
          <div class="media">
               <div class="media-content">
                 <label class="label">{{titulo_filme}}</label>
                 <p class="subtitle is-6">{{filme.avaliacao}}      {{filme.genero}}</p>
                 <p class="subtitle is-7">R$ {{filme.valor}}</p>
              </div>
         </div>

         <div class="content">
      
         </div>    
     </div>   
     <div class="buttons">
       <button class="button is-link is-normal is-fullwidth">Adicionar</button>
     </div>   
 </div>
</template>

<script>
import axios from 'axios';

export default {
    created: function(){
       axios.get("https://api.themoviedb.org/3/movie/"+this.id_filme+"?api_key=b02c26e7cdf8332f6747485120b222dc&language=pt-BR").then(res => {
           //console.log(res);
            this.filme.genero = res.data.genres[0].name;
            this.filme.datalan = res.data.release_date;
            this.filme.avaliacao = res.data.vote_average;
            this.filme.caminhocapa = res.data.poster_path;
            this.filme.capa = "https://image.tmdb.org/t/p/original"+this.filme.caminhocapa;
            this.filme.valor = 79.99;
            console.log(this.filme);
       })
    },
    data(){
         return {
            filme: {
              genero: '',
              datalan: '',
              avaliacao: 0,
              capa: '',
              valor: 0
            }
         }
    },
    props: {
        num: Number,
        titulo_filme: String,
        id_filme: Number
    },
    methods: {
        
    }

}
</script>

<style>
   #filme{
    margin-bottom: 1.5rem;
    width:200px;
    height:550px;
   }
</style>