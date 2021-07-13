<template>
  <header>
    <div class="container">
      <div class="row bg-dark">
        <div class="col d-flex justify-content-between align-items-center">
          <img src="@/assets/boolflix.png" alt="logo BoolFlix">
          <input type="text" v-model="searchText" @keyup.enter="$emit('search', searchText)" name="search" id="search" placeholder="Inserisci il titolo del film" class="text-center text-white">
        </div>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  name: 'Header',
  data() {
    return {
      searchText: ''
    }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
header{
  height: 100px;
}

img{
  height: 100px;
}

input{
  background-color: #303030;
  border: 2px white solid;
}

input::placeholder{
  color: grey;
}
</style>
