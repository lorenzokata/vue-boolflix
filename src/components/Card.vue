<template>
  <div class="col py-2 px-1">
    <div class="card">
      <img :src="getImgPath()" alt="" class="card-img-top position-relative">
      <div class="card-body position-absolute">
        <div class="title">{{ content.title || content.name }}</div>
        <div class="subtitle text-muted" v-if="content.original_title != content.title || content.original_name != content.name">{{ content.original_title || content.original_name }}</div>
        <div class="language mt-2 mb-2 d-flex align-items-center justify-content-around">
          <img :src="getFlagURL()" class="language-flag" :alt="content.original_language">
          <div class="rating"><star-rating star-size="20" :read-only=true :rating="Math.round((content.vote_average)/2)" :show-rating="false"/></div>
        </div>
        <div class="overview" v-if="content.overview">{{content.overview}}</div>
        <div class="overview" v-else>Informazioni non disponibili</div>
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
.col{
  height: 401.5px;
}

.card{
  border: none;
  height: 100%;
}

.card:hover .card-body{
  display: block;
}

.card-img-top{
  filter: brightness(1);
  transition: all 0.5s ease;
}

.card:hover .card-img-top{
  filter: brightness(20%)	;
}

.card-body *{
  color: white;
  font-size: 14px;
}

.card-body{
  background-color:none;
  height: 100%;
  display: none;
  overflow: auto;
}

.card-body::-webkit-scrollbar {
  display: none;
}

.title{
  font-size: 20px;
}

.language-flag{
  width: 20%;
}

</style>
S