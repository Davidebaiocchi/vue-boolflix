<template>
  <div class="card">
    <div class="cover">
      <img :src="imgBaseURL + imgBaseDimension + serie.poster_path" :alt="'Copertina ' + serie.name">
    </div>
    <div class="description">
      <span class="titolo"> {{ serie.name }} </span>  <br>
      <span class="titolo-or"> '{{ serie.original_name }}' </span> <br>
      <span> Voto: {{ serie.vote_average }} </span> <br>
      <span class="lingua"> Lingua: <img :src="getImgUrl(language)" v-bind:alt="language"> </span> 
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

  img {
    height: 15px;
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
    background-color: rgba(0, 0, 0, 0.911);
    height: 100%;
    width: 100%;
    text-transform: uppercase;
    font-weight: 900;
  }

  .titolo {
    font-size: 40px;
    color: crimson;
  }

  .titolo-or, .lingua {
    font-size: 20px;
  }
</style> 