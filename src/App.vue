<template>
  <div id="app">
    
    <Header @query="search"/>
    <main>
      <Film 
        v-for="(film, index_film) in films"
        :key="index_film"
        :movie="film"
        class='hide'
      />
      <Serie 
        v-for="(serie, index_serie) in series"
        :key="index_serie"
        :serie="serie"
      />
    </main>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Film from './components/Film.vue'
import Serie from './components/Series.vue'
import axios from 'axios';

export default {
  name: 'App',
  data(){
    return{
      films:[],
      series:[],
    }
  },
  components: {
    Header,
    Film,
    Serie
  },
  methods:{
    search(query){
      axios.get('https://api.themoviedb.org/3/search/movie/?api_key=a095e7fba1e47219b477d93c8457cf97&language=it-IT&query=' + query)
    .then(res=> {
      this.films = res.data.results
      console.log(this.films)
      console.log('ciao')
    })
    .catch(err=>{
      console.log(err)
    })
    axios.get('https://api.themoviedb.org/3/search/tv/?api_key=a095e7fba1e47219b477d93c8457cf97&language=it-IT&query=' + query)
    .then(res=> {
      this.series = res.data.results
      console.log(this.series)
      console.log('ciao')
    })
    .catch(err=>{
      console.log(err)
    })
    }
  }
}
</script>

<style lang="scss">
#app {
@import url('../assets/general.scss');
main{
  height:100%;
  width:100%;
  background-color: yellowgreen;
}
.hide{
  display:none;
}
}
</style>
