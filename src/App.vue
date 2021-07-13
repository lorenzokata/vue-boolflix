<template>
  <div id="app">
    <Header @search="searchContent"/>
    <Main :films="films"/>
  </div>
</template>

<script>
import Header from './components/Header.vue';
import Main from './components/Main.vue';
import axios from 'axios'


export default {
  name: 'App',
  components: {
    Header,
    Main
  },
  data() {
    return {
      apiURL: 'https://api.themoviedb.org/3/search/movie',
      apiKey: 'b0f7a2f27387a19f6c3cd6159d727ecd',
      language: 'it-IT',
      films: []
    }
  },
  methods:{
    searchContent(searchText){
      axios
      .get(this.apiURL, {
        params:{
          api_key: this.apiKey,
          language: this.language,
          query: searchText
        }
      })
      .then( response =>{
        this.films = response.data.results;
      })
      searchText=''
    }
  }
}
</script>

<style lang="scss">

  @import "@/style/commons.scss"

</style>
