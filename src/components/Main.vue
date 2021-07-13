<template>
  <main class="py-3">
    <div class="container">
      <div class="row row-cols-2 row-cols-md-3 row-cols-lg-4 row-cols-xl-5">
      <Card v-for="film in films" :key="film.id" :film="film"/>
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
    films: Array
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>
