<template>
  <div class="col py-2 px-1">
    <div class="card">
      <img :src="getImgPath()" alt="" class="card-img-top position-relative">
      <div class="card-body position-absolute">
        <div class="card-title">{{ content.title || content.name }}</div>
        <div class="card-subtitle mb-2 text-muted">{{ content.original_title || content.original_name }}</div>
        <div class="list-group-item language">
          <img :src="getFlagURL()" class="language-flag" :alt="content.original_language">
        </div>
        <div class="list-group-item vote"><star-rating star-size="20" :read-only=true :rating="Math.round((content.vote_average)/2)" :show-rating="false"/></div>
      </div>
    </div>
  </div>
</template>

<script>

import StarRating from 'vue-star-rating'

export default {
  name: 'Card',
  components:{
    StarRating
  },
  props: {
    content: Object
  },
  data() {
    return {
      flagURL:'',
    }
  },
  methods: {
    getFlagURL(){
      if (this.content.original_language == 'en') {
        return this.flagURL=require('@/assets/en.png')
      } else{
        return this.flagURL='https://www.countryflags.io/' + this.content.original_language + '/shiny/64.png'
      }
    },
    getImgPath(){
      return (this.content.poster_path ? 'https://image.tmdb.org/t/p/w342' + this.content.poster_path : require('@/assets/notavailable.jpg'))
    }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.card{
  border: 1px solid black;
}

.language-flag{
  width: 20%;
}

list-group-item svg{
  height: 10px;
}
</style>
S