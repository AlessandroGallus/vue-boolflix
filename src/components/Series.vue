<template>
  <div class="serie">
    <p>{{serietv.name}}</p>
    
  </div>
</template>

<script>
export default {
  props:{
    serietv:Object
  }
}
</script>

<style>
  .serie{
    width:100%;
    height: 200px;
    background-color: green;
  }
</style>