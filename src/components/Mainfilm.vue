<template>
  <div>
      <h2>I MIEI FILM</h2>
        <div class="container">
            <div class="row">
                <div class="col big-box" v-for="(film,index) in films" :key="index" >
                    <div class="film-box">
                            <div class="img-box"><img :src="'https://image.tmdb.org/t/p/w300'+film.poster_path" alt=""></div>
                            <div class="show">
                                <div>{{film.title}} </div>
                                <div>{{film.original_title}}  </div>
                                <div class="bandiera"><img :src="'/assets/'+ film.original_language.toLowerCase()+'.png'"> </div>
                                <div>{{film.vote_average}} </div>
                            </div>
                    </div>
                </div>

            </div>
        </div>
        

  <!--         <h2>LE MIE SERIE TV</h2>
            <div class="container">
                <div class="row">
                    <div class="col-3 big-box" v-for="(serie,index) in serielist" :key="index" >
                    <div class="film-box" v-if="serie.name.toLowerCase().includes(ric.toLowerCase())">
                        <div>{{serie.name}} </div>
                        <div>{{serie.original_name}}  </div>
                        <div class="bandiera"><img :src="'/assets/'+ serie.original_language.toLowerCase()+'.png'"></div>
                        <div>{{serie.vote_average}} </div>
                </div>

                </div>
            </div> -->


  </div>
</template>

<script>
export default {
    data(){
        return{
/*             apiFilmUrl: 'https://api.themoviedb.org/3/search/movie?api_key=e4f1a7e862417c6e22ee5a0fffab8242&language=en-US&page=1&include_adult=false&query=', */
            /* https://api.themoviedb.org/3/search/movie?api_key=e4f1a7e862417c6e22ee5a0fffab8242&language=en-US&page=1&include_adult=false&query=matrix */
            /* filmlist:[],
            apiSerieUrl:'https://api.themoviedb.org/3/search/tv?api_key=e99307154c6dfb0b4750f6603256716d&language=it_IT&query=s',
            serielist:[], */
        }
    },
    props:{
        films : Array,
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
        &:hover{
            background-color: lightgray;
            .img-box{
                display: none;
            }
            .show{
            display: inline-block;
            height: 450px;
            width: 300px;
            
        }
        }
        border-radius: 5px ;
        .show{
            display: none;
        }
        .bandiera{
            height: 30px;
            width: 30px;
            img{
                height: 30px;
                width: 30px;
            }
        }
        }
    }

</style>