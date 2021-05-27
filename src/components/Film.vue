<template>
  <div class="film">
    
    <p>{{movie.title}}</p>
    <p>{{movie.original_title}}</p>
    <!-- <p><img src="../assets/flag_it.jpg" alt=""></p> -->
    <p><img :src="changeimage(movie.original_language)" :alt="movie.original_language"></p>
    <p>{{movie.vote_average}}</p>
    <p>{{movie.overview}}</p>
  </div>
</template>

<script>
export default {
  props:{
    movie:Object,
  },
  data(){
    return{
      original_language:''
    }
  },

  methods:{
    changeimage(ol){
      let str = '../assets/flag_' + ol + '.jpg'
      console.log(str)
     return(str)
    }
  }
}
</script>

<style lang="scss">
  .film{
    width:100%;
    height: 200px;
    background-color: yellow;
    img{
      width:50px;
    }
  }
</style>