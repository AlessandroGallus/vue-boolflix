<template>
  <div class="film">
    <p>{{movie.title}}</p>
    <p>{{movie.original_title}}</p>
    <p>{{movie.original_language}}</p>
    <p>{{movie.vote_average}}</p>
  </div>
</template>

<script>
export default {
  props:{
    movie:Object
  }
}
</script>

<style>
  .film{
    width:100%;
    height: 200px;
    background-color: yellow;
  }
</style>