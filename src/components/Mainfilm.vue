<template>
  <div>
      <h2>I MIEI FILM</h2>
        <div class="big-box" v-for="(film,index) in filmlist" :key="index" >
            <div class="film-box" v-if="film.title.toLowerCase().includes(ric.toLowerCase())">
                    <div>{{film.title}} </div>
                    <div>{{film.original_title}}  </div>
                    <div>{{film.original_language}} <img :src="'https://www.countryflags.io/'+'film.origin_language'+'/flat/64.png'"> </div>
                    <div>{{film.vote_average}} </div>
            </div>
        </div>

          <h2>LE MIE SERIE TV</h2>

            <div class="big-box" v-for="(serie,index) in serielist" :key="index" >
            <div class="film-box" v-if="serie.name.toLowerCase().includes(ric.toLowerCase())">
                <div>{{serie.name}} </div>
                <div>{{serie.original_name}}  </div>
                <div><img :src="'https://www.countryflags.io/'+ serie.origin_country[0].toLowerCase()+'/flat/64.png'"></div>
                <div>{{serie.vote_average}} </div>
          </div>

      </div>
  </div>
</template>

<script>
import axios from 'axios';
export default {
    data(){
        return{
            apiFilmUrl: 'https://api.themoviedb.org/3/movie/popular?api_key=e074c01e562b214f49b0d0b915aa74f1',
            filmlist:[],
            apiSerieUrl:'https://api.themoviedb.org/3/search/tv?api_key=e99307154c6dfb0b4750f6603256716d&language=it_IT&query=s',
            serielist:[],
        }
    },
    props:{
        ric : String,
    },
    created(){
        this.getFilms();
        this.getSeries();
    },
    methods:{
        getFilms(){
            axios
                .get(this.apiFilmUrl)
                .then(response =>{
                    this.filmlist= response.data.results;
                    console.log(this.filmlist);
                })
        },
        getSeries(){
            axios
                .get(this.apiSerieUrl)
                .then(response =>{
                    this.serielist=response.data.results;
                    console.log(this.serielist);
                })
        }
    }
}
</script>

<style lang="scss" scoped>
    .big-box{
        display: inline-flex;
        .film-box{
        margin: 8px;
        padding: 5px;
        border: 3px solid rgb(167, 3, 3);
        background-color: lightgray;
        border-radius: 5px ;
        height: 200px;
        width: 200px;
        }
    }
</style>