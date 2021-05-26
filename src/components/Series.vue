<template>
  <div class="serie">
    <p>{{serie.name}}</p>
    
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