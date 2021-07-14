<template>
  <div class="card">
    <div class="cover">
      <img :src="imgBaseURL + imgBaseDimension + film.backdrop_path" :alt="'Copertina ' + film.title">
    </div>
    <div class="description">
      Titolo = {{film.title}} <br>
      Titolo originale = {{film.original_title}} <br>
      Lingua = <img :src="getImgUrl(language)" v-bind:alt="language"> <br>
      Voto = {{film.vote_average}} <br>
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
    }
  }
}
</script>
