<template>
  <div id="app">
    <Ricerca @search="ricercaFilm"/>
    <Mainfilm :films="films" :series="serie"/>
  </div>
</template>

<script>
import Mainfilm from './components/Mainfilm.vue'
import Ricerca from './components/Ricerca.vue'
import axios from 'axios'
export default {
  name: 'App',
  data(){
    return{
      apiURL: 'https://api.themoviedb.org/3/search/movie',
      apiURLserie: 'https://api.themoviedb.org/3/search/tv',
      apiKey: 'e4f1a7e862417c6e22ee5a0fffab8242',
      language: 'it-IT',
      films: [],
      serie:[]
    }
  },
  components: {
    Mainfilm,
    Ricerca
  },

  methods:{
    ricercaFilm(str){
               axios
                .get(this.apiURL,{
                  params:{
                    api_key:this.apiKey,
                    language: this.language,
                    query:str
                  }
                })
                .then(response =>{
                    this.films= response.data.results;
                    console.log(this.films);
                });
              axios
                .get(this.apiURLserie,{
                  params:{
                    api_key:this.apiKey,
                    language:this.language,
                    query:str
                  }
                })
                .then(response =>{
                  this.serie= response.data.results;
                    console.log(this.serie);
                })
    },
 
  }
}
</script>

<style lang="scss">
@import '@/style/general.scss';
</style>
