<template>
  <div>
      <div v-for="(film,index) in filmlist" :key="index">
          <div class="film-box">
          {{film.title}}
          {{film.original_title}}
          {{film.original_language}}
          {{film.vote_average}}
          </div>

      </div>
  </div>
</template>

<script>
import axios from 'axios';
export default {
    data(){
        return{
            apiUrl: 'https://api.themoviedb.org/3/movie/popular?api_key=e074c01e562b214f49b0d0b915aa74f1',
            filmlist:[],
        }
    },
    created(){
        this.getFilms();
    },
    methods:{
        getFilms(){
            axios
                .get(this.apiUrl)
                .then(response =>{
                    this.filmlist= response.data.results;
                    console.log(this.filmlist);
                })
        }
    }
}
</script>

<style lang="scss">
    .film-box{
        display: inline-flex;
        flex-direction: initial;
        height: 200px;
        width: 200px;
    }
</style>