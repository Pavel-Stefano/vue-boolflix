<template>
  <div id="app">
    <header>
       <h1 class="text-center">Boolflix</h1>
      <search-bar @performSearch="search" />
    </header>

    <main>
      <list-grid :items="movies" title="Movies" :loader="loading" />
      <list-grid :items="series" title="Series" :loader="loadingSeries" />
      
      
    </main>
   
  </div>
</template>

<script>
import ListGrid from './components/ListGrid.vue'
import SearchBar from './components/SearchBar.vue'

import axios from 'axios'


export default {  
  name: 'App',
  components: {
    SearchBar,
    ListGrid,
    
  },
  data(){
    return {
      movies: [],
      series: [],
      apiPath: 'https://api.themoviedb.org/3/search/',
      apiKey: 'f663e88b1d121111af7e625dad4ef3a7',
      loading: false,
      loadingSeries: false,
      title: false,
    }
  },
  methods: {
    // chiamata api
    getMovies(queryParams){
      // const queryParams = {
      //   params: {
      //     api_key: this.apiKey,
      //     query: '',
      //   }
      // }
      axios.get(this.apiPath+'movie',queryParams).then((res)=>{
        // console.log(res)
        this.movies = res.data.results;
        this.loading = false;
      }).catch((error)=>{
        console.log(error);
      })
    },
    getSeries(queryParams){
      axios.get(this.apiPath+'tv',queryParams).then((res)=>{
        // console.log(res)
        this.series = res.data.results;
        this.loadingSeries = false;
      }).catch((error)=>{
        console.log(error);
      })
    },
    // funzione cerca
    search(text){
      // console.log(text)
      const queryParams = {
        params: {
          api_key: this.apiKey,
          query: text,
        }
      }
      this.loading = true;
      this.loadingSeries = true;
      this.getMovies(queryParams);
      this.getSeries(queryParams);
    }
  },
}
</script>

<style lang="scss">
@import './style/general.scss';
</style>
