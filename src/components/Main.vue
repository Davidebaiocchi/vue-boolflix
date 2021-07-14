<template>
  <main>
    <div class="container">

      <div class="Cards">

        <CardSerieTv 
        v-for="(serie, i) in serieArray"
        :key="i"
        :serie="serie"
        :imgBaseURL="imgBaseURL"
        :imgBaseDimension="imgBaseDimension"/>

        <CardFilm 
        v-for="(film, i) in filmArray"
        :key="i"
        :film="film"
        :imgBaseURL="imgBaseURL"
        :imgBaseDimension="imgBaseDimension"/>

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
  }
</style>
