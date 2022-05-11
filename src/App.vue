<template>
  <div id="app">
    <header>
       <h1 class="text-center">Boolflix</h1>
      <search-bar />
    </header>

    <main>

    </main>
   
  </div>
</template>

<script>
import SearchBar from './components/SearchBar.vue'


export default {  
  name: 'App',
  components: {
    SearchBar,
    
  },
  data(){
    return {

    }
  }
}
</script>

<style lang="scss">
@import './style/general.scss';
</style>
