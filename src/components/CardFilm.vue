<template>
  <div class="card">
    <div class="cover">
      <img v-if="film.backdrop_path == null" src="@/assets/img/images.jpg" alt="cover">
      <img :src="imgBaseURL + imgBaseDimension + film.backdrop_path" alt="">
    </div>
    <div class="description">
      <span class="titolo"> {{film.title}} </span> <br>
      <span class="titolo-or"> '{{film.original_title}}' </span> <br>
      <span class="lingua"> <img :src="getImgUrl(language)" v-bind:alt="language"> 
      <!-- stelle piene -->
      <i class="piene fas fa-star"
      v-for="(star,i) in loadStars(film.vote_average)" :key="i"
      ></i>

      <!-- stelle vuote -->
      <i class="far fa-star"
      v-for="(star,i) in loadEmptyStars(film.vote_average)" :key="i"
      ></i></span> 

      <div class="riassunto">
        riassunto:
        Lorem ipsum dolor sit amet consectetur, adipisicing elit. Commodi, aliquid perferendis exercitationem sapiente nulla sequi amet accusamus fuga eos voluptatum, obcaecati eligendi at perspiciatis cumque saepe, optio earum vero ipsam.
      </div>
      
    </div> 
  </div>
</template>

<script>
export default {
  name : 'CardFilm',
  props : ['film','imgBaseURL','imgBaseDimension'],
  data(){
    return {
      language: this.film.original_language
    }
  },
  methods : {
    getImgUrl(pic) {
      try {
        let fileName = require('../assets/img/' + pic + '.png');
        return fileName
      } 
      catch (none) {
        return 'none'
      }  
    },
    loadStars(vote){
      return Math.round(vote / 2)
    },
    loadEmptyStars(vote){
      return 5 - (Math.round(vote / 2))
    }
  }
}
</script>
