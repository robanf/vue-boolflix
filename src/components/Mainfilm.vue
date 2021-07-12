<template>
  <div>
      <div class="film-box" v-for="(film,index) in filmlist" :key="index">
          <div>
                <div>{{film.title}} </div>
                <div>{{film.original_title}}  </div>
                <div>{{film.original_language}} </div>
                <div>{{film.vote_average}} </div>
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
        margin: 5px;
        display: inline-flex;
        
        border: 2px solid black;
        height: 200px;
        width: 200px;
    }
</style>