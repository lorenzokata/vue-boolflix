<template>
  <div id="app">
    <Header @search="searchContent"/>
    <Main :films="films" :series="series"/>
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
      apiFilmsURL: 'https://api.themoviedb.org/3/search/movie',
      apiSeriesURL:'https://api.themoviedb.org/3/search/tv',
      apiKey: 'b0f7a2f27387a19f6c3cd6159d727ecd',
      language: 'it-IT',
      films: [],
      series:[]
    }
  },
  methods:{
    searchContent(searchText){
      // RICERCA FILM
      axios
      .get(this.apiFilmsURL, {
        params:{
          api_key: this.apiKey,
          language: this.language,
          query: searchText
        }
      })
      .then( response =>{
        this.films = response.data.results;
      })
      // RICERCA SERIE TV
      axios
      .get(this.apiSeriesURL, {
        params:{
          api_key: this.apiKey,
          language: this.language,
          query: searchText
        }
      })
      .then( response =>{
        this.series = response.data.results;
      })
      searchText=''
    }
  }
}
</script>

<style lang="scss">

  @import "@/style/commons.scss"

</style>
