<template>
  <div>
      <h2>I MIEI FILM</h2>
        <div class="container">
            <div class="row">
                <div class="col-3 big-box" v-for="(film,index) in films" :key="index" >
                    <div class="film-box">
                            <div class="img-box"><img :src="'https://image.tmdb.org/t/p/w300'+film.poster_path" onerror="this.src='/assets/img404.jpg'"
 alt=""></div>
                            <div class="show">
                                <div>{{film.title}} </div>
                                <div>{{film.original_title}}  </div>
                                <div class="bandiera"><img :src="'/assets/'+ film.original_language.toLowerCase()+'.png'"> </div>
                                <div class="fa fa-star"><star-rating :star-size=26 :rating="Math.round((film.vote_average)/2)"></star-rating>  </div>
                                <div class="trama">TRAMA={{film.overview}}</div>
                            </div>
                    </div>
                </div>

            </div>
        </div>
        

          <h2>LE MIE SERIE TV</h2>
            <div class="container">
                <div class="row">
                    <div class="col-3 big-box" v-for="(serie,index) in series" :key="index" >
                    <div class="film-box">
                        <div class="img-box"> <img :src="'https://image.tmdb.org/t/p/w300'+ serie.poster_path" onerror="this.src='/assets/img404.jpg'" alt=""></div>
                        <div class="show">
                            <div>{{serie.name}} </div>
                            <div>{{serie.original_name}}  </div>
                            <div class="bandiera"><img :src="'/assets/'+ serie.original_language.toLowerCase()+'.png'"></div>
                            <div id="voto"><star-rating :star-size=26 :rating="Math.round((serie.vote_average)/2)"></star-rating> </div>
                            <div class="trama">TRAMA={{serie.overview}}</div>
                        </div>
                </div>

                </div>
            </div>
            </div>


  </div>
</template>

<script>
import StarRating from 'vue-star-rating'
export default {
    data(){
        return{
/*             apiFilmUrl: 'https://api.themoviedb.org/3/search/movie?api_key=e4f1a7e862417c6e22ee5a0fffab8242&language=en-US&page=1&include_adult=false&query=', */
            /* https://api.themoviedb.org/3/search/movie?api_key=e4f1a7e862417c6e22ee5a0fffab8242&language=en-US&page=1&include_adult=false&query=matrix */
            /* filmlist:[],
            apiSerieUrl:'https://api.themoviedb.org/3/search/tv?api_key=e99307154c6dfb0b4750f6603256716d&language=it_IT&query=s',
            serielist:[], */
            temp:2
        }
    },
    components: {
        StarRating
    },
    props:{
        films : Array,
        series: Array,
    },
}
</script>

<style lang="scss" scoped>
    div{
        background-color: rgb(22, 22, 22);
        h2{
            color: rgb(167, 3, 3);
        }

    .big-box{
        display: inline-flex;
        .film-box{
        margin: 8px;
        padding: 5px;
        border: 3px solid rgb(167, 3, 3);
        border-right:3px solid rgb(167, 3, 3) ;
        &:hover{
            background-color: rgb(22, 22, 22);
            color: white;
            .img-box{
                display: none;
            }
            .show{
            display: inline-block;
            height: 450px;
            width: 300px;
            
        }
        }
        .trama{
            font-size: 12px;
        }
            .img-box{
                height: 450px;
                width: 300px;
                img{
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
    }

</style>