<template>
  <div id="app">
    <Ricerca @search="ricercaFilm"/>
    <Mainfilm :ric="ricercato"/>
  </div>
</template>

<script>
import Mainfilm from './components/Mainfilm.vue'
import Ricerca from './components/Ricerca.vue'

export default {
  name: 'App',
  data(){
    return{
      ricercato:"",
    }
  },
  components: {
    Mainfilm,
    Ricerca
  },
  methods:{
    ricercaFilm(str){
      console.log(str);
      this.ricercato=str;
    }
  }
}
</script>

<style lang="scss">
@import '@/style/general.scss';
</style>
