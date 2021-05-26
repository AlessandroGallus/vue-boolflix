<template>
  <header>
    <input type="text" @keyup.enter="search" v-model="query">
    <button @click.prevent="search">
      Search
    </button>
  </header>
</template>

<script>
export default {
  name: 'Header',
  data(){
    return{
      query:''
    }
  },
  methods:{
    search(){
      this.$emit("query", this.query)
    }
  },
  props: {
    
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
header{
  height:120px;
  width: 100%;
  background-color: grey;
}
</style>
