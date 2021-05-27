<template>
  <div id="app">
    
    <Header 
    @query="search"
    @language="changeLanguage"
    @switch_value="changeType"
    />
    <main>
      <div class="films">
        <Film 
        v-for="(film, index_film) in films"
        :key="index_film"
        :class="(show_films) ? 'show' : 'hide'"
        :movie="film"
      />
      </div>
      <div class="series">
        <Serie 
        v-for="(serie, index_serie) in series"
        :key="index_serie"
        :class="(show_series) ? 'show' : 'hide'"
        :serietv="serie"
      />
      </div>
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
      show_films:true,
      show_series:true,
      query_search:'',
      films:[],
      series:[],
      lang:'it-IT'
    }
  },
  components: {
    Header,
    Film,
    Serie
  },
  methods:{
    search(query){
      this.query_search = query
      axios.get('https://api.themoviedb.org/3/search/movie/?api_key=a095e7fba1e47219b477d93c8457cf97&language='+this.lang+'&query=' + query)
    .then(res=> {
      this.films = res.data.results
      console.log(this.films)
    })
    .catch(err=>{
      console.log(err)
    });
    axios.get('https://api.themoviedb.org/3/search/tv/?api_key=a095e7fba1e47219b477d93c8457cf97&language=it-IT&query=' + query)
    .then(ress=> {
      this.series = ress.data.results
      console.log(this.series)
    })
    .catch(errr=>{
      console.log(errr)
    })
    },
    changeLanguage(language){
      this.lang = language
      console.log(language)
      this.search(this.query_search)
    },
    changeType(value){
      console.log(value)
      if(value == 2){
        this.show_films=true
        this.show_series=false
      }else if(value == 3){
        this.show_series=true
        this.show_films=false
      }else {
        this.show_films=true
        this.show_series=true
      }
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
.show{
  display: block;
}
.hide{
  display:none;
}
}
</style>
