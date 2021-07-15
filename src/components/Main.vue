<template>
  <main>
    <div class="container">
      <div class="Cards">
        <div class="container" v-if="filmArray.lenght !==0 && serieArray.lenght !==0">
          <CardSerieTv 
          v-for="(serie, index) in serieArray"
          :key="index"
          :serie="serie"
          :imgBaseURL="imgBaseURL"
          :imgBaseDimension="imgBaseDimension"/>

          <CardFilm 
          v-for="(film, index) in filmArray"
          :key="index"
          :film="film"
          :imgBaseURL="imgBaseURL"
          :imgBaseDimension="imgBaseDimension"/>
        </div> 
      </div>
    </div>
  </main>
</template>

<script>
import CardFilm from '@/components/CardFilm.vue';
import CardSerieTv from '@/components/CardSerieTv.vue';

export default {
  name : 'Main',
  components : {
    CardFilm,
    CardSerieTv
  },
  props : ['searchText', 'filmArray', 'serieArray', 'imgBaseURL', 'imgBaseDimension']
}
</script>

<style lang="scss">
  main{
    padding: 30px 0;
    height: 100vh;
    overflow-y: scroll;
    padding-top: 80px;
    background-color: #141414;
    color: white;
    .Cards{
      margin-top: 50px;
      display: flex;
      flex-wrap: wrap;
      padding-left: 30px;
      width: 100%;
    }

    .container {
      display: flex;
      flex-wrap: wrap;
    }
  }
</style>
