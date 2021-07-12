<template>
  <div>
      <input type="text" placeholder="cerca il film" 
      v-model="inputText"
      :onchange="$emit('search', inputText)"
      >
  </div>
</template>

<script>
export default {
    data(){
        return{
            inputText:"",
        }
    }
}
</script>

<style lang="scss" scoped>
    input{
        margin: 10px;
        padding: 5px;
        border: 3px solid rgb(167, 3, 3);
        border-radius: 5px ;
    }
</style>