<template>
  <div class="col p-2">
    <div class="card p-1">
    <!-- <img :src="film." alt="" class="card-img-top"> -->
    <div class="card-title">{{ film.title }}</div>
    <div class="card-subtitle mb-2 text-muted">{{ film.original_title }}</div>
    <div class="list-group-item language">{{ film.original_language }}</div>
    <div class="list-group-item vote">{{ film.vote_average }}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Card',
  props: {
    film: Object
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.card{
  border: 1px solid black;
}
</style>
