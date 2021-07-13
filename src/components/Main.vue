<template>
  <main class="py-3">
    <div class="container">
      <div class="films">
        <h1 v-if="films.length != 0" class="text-danger">FILM</h1>
        <div class="row row-cols-2 row-cols-md-3 row-cols-lg-4 row-cols-xl-5">
          <Card v-for="film in films" :key="film.id" :content="film"/>
        </div>
      </div>
      <div class="series">
        <h1 v-if="series.length != 0" class="text-danger">SERIE TV</h1>
        <div class="row row-cols-2 row-cols-md-3 row-cols-lg-4 row-cols-xl-5">
          <Card v-for="serie in series" :key="serie.id" :content="serie"/>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
import Card from './Card.vue'

export default {
  name: 'Main',
  components:{
    Card
  },
  props: {
    films: Array,
    series: Array
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
main{
  height: calc(100vh - 100px);
  overflow: auto;
  background-color: #141414;
}
</style>
