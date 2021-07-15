<template>
  <div class="card">

    <!-- copertina card -->
    <div class="cover">
      <img v-if="film.backdrop_path == null" src="@/assets/img/images.jpg" alt="cover">
      <img v-else :src="imgBaseURL + imgBaseDimension + film.backdrop_path" alt="">
    </div>

    <!-- descrizione card -->
    <div class="description">
      <span class="titolo"> {{film.title}} </span> <br>
      <span v-if="film.title !== film.original_title" class="titolo-or"> '{{film.original_title}}' </span> <br>
      <span class="lingua"> <img :src="getImgUrl(language)" v-bind:alt="language"> 

      <!-- stelle piene -->
      <i class="piene fas fa-star"
      v-for="(star, i) in stars(film.vote_average)" :key="i"
      ></i>

      <!-- stelle vuote -->
      <i class="far fa-star"
      v-for="(star, index) in whiteStars(film.vote_average)" :key="index"
      ></i></span> 

      <div class="riassunto">
        <span v-if="film.overview === ''"></span>
        <span v-else> {{ film.overview }} </span>
      </div>
    <!-- fine descrizione card -->
      
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
    // funzione per prendere le copertine delle card
    getImgUrl(pic) {
      try {
        let fileName = require('../assets/img/' + pic + '.png');
        return fileName
      } 
      catch (none) {
        return 'none'
      }  
    },
    // funzione per le stelle gialle
    stars(vote){
      return Math.round(vote / 2)
    },
    // funzione per le stelle vuote
    whiteStars(vote){
      return 5 - (Math.round(vote / 2))
    }
  }
}
</script>
