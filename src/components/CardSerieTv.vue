<template>
  <div class="card">
    <div class="cover">
      <img v-if="serie.poster_path == null" src="@/assets/img/images.jpg" alt="cover">
      <img v-else :src="imgBaseURL + imgBaseDimension + serie.poster_path" alt="">
    </div>
    <div class="description">
      <span class="titolo"> {{ serie.name }} </span>  <br>
      <span v-if="serie.name !== serie.original_name"  class="titolo-or"> '{{ serie.original_name }}' </span> <br>
      <span class="lingua"><img :src="getImgUrl(language)" v-bind:alt="language">  
      <!-- stelle piene -->
      <i class="piene fas fa-star"
      v-for="(star, index) in stars(serie.vote_average)" :key="index"
      ></i>

      <!-- stelle vuote -->
      <i class="far fa-star"
      v-for="(star, index) in whiteStars(serie.vote_average)" :key="index"
      ></i></span> 

      <div class="riassunto">
        <span v-if="serie.overview === ''"></span>
        <span v-else> {{ serie.overview }} </span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name : 'CardSerieTv',
  props : ['serie', 'imgBaseURL', 'imgBaseDimension'],
  data(){
    return{
      language : this.serie.original_language
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
    stars(vote){
      return Math.round(vote / 2)
    },
    whiteStars(vote){
      return 5 - (Math.round(vote / 2))
    }
  }
}
</script>

<style lang="scss">
  .card{
    width: 300px;
    margin-right: 10px;
    height: 500px;
    margin-bottom: 50px;
    position: relative;
    cursor: pointer;
  }

  .cover{
    img{
      height: 500px;
      width: 300px;
      object-fit: cover;
    }
  }

  .description {
    position: absolute;
    top: 0;
    left: 0;
    z-index: -1;
    font-size: 25px;
    padding: 20px;
    text-align: center;
  }

  .card:hover .description {
    z-index: 1;
    background-color: rgba(0, 0, 0, 0.931);
    height: 100%;
    width: 100%;
    text-transform: uppercase;
    font-weight: 900;
  }

  .titolo {
    font-size: 30px;
    color: crimson;
  }

  .titolo-or {
    font-size: 16px;
  }

  .lingua img {
    margin-right: 40px;
    height: 25px;
    margin-top: 30px;
    position: relative;
    top: 5px;
  }

  .piene {
    color: gold;
  }

  .riassunto {
    overflow-y: scroll;
    height: 200px;
    margin-top: 40px;
    font-size: 15px;
    font-weight: 400;
  }

</style> 