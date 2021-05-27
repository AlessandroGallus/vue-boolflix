<template>
  <header>
    <div class="searchbar">
      <input type="text" @keyup.enter="search" v-model="query">
      <button @click.prevent="search">
        Search
      </button>
    </div>
    <div class="language_and_select">
      <img 
        src="../assets/flag_it.jpg"
        alt="bandiera italiana"
        @click.prevent="switchIta"
        >
      <select name="Tipo" id="tipo" v-model="switch_value" @change="switchType">
        <option value="1" selected>All</option>
        <option value="2">Movies</option>
        <option value="3">TV Series</option>
      </select>
      <img 
        src="../assets/flag_en.jpg" 
        alt="bandiera UK" 
        @click.prevent="switchEng">
    </div>
  </header>
</template>

<script>
export default {
  name: 'Header',
  data(){
    return{
      query:'',
      switch_value:1,
      language:'it-IT'
    }
  },
  methods:{
    search(){
      this.$emit("query", this.query)
      this.query=''
    },
    switchIta(){
      this.language='it-IT'
      this.$emit("language", this.language)
      console.log(this.language)
    },
    switchEng(){
      this.language='en-EN'
      this.$emit("language", this.language)
      console.log(this.language)
    },
    switchType(){
      this.$emit("switch_value", this.switch_value)
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
  .searchbar{
    width: 70%;
    height:50%;
    margin:0 auto;
    display: flex;
    input{
      width: 92%;
      height: 80%;
      margin: auto 0;
      font-size: 30px;
    }
    button{
      width: 8%;
      height: 80%;
      margin: auto 0;
    }
  }
  .language_and_select{
    width: 70%;
    height:50%;
    margin:0 auto;
    display: flex;
    justify-content: space-around;
    align-items: center;
    cursor: pointer;
    img{
      height:60%;
    }
  }
}
</style>
