<template>
  <div id="app">
    <Header @startTest="searchInAPI"/>
    <Main 
    :filmArray="filmArray" 
    :serieArray="serieArray" 
    :imgBaseURL="imgBaseURL" 
    :imgBaseDimension="imgBaseDimension"
    :searchText="searchText"/>
  </div>
</template>


<script>
import Header from './components/Header.vue';
import Main from './components/Main.vue';
import axios from 'axios';
export default {
  name: 'App',
  components: {
    Header,
    Main
  },
  data(){
    return{
      apiURLFilm : 'https://api.themoviedb.org/3/search/movie?',
      apiURLSerie : 'https://api.themoviedb.org/3/search/tv?',
      filmArray : [],
      serieArray : [],
      defaultView : [],
      imgBaseURL : 'https://image.tmdb.org/t/p/',
      imgBaseDimension : 'original',
      searchText : ''
    }
    
  },
  methods : {
    searchInAPI(inputText){
      this.searchFilm(inputText);
      this.searchSerie(inputText);
    },

    // funzione per cercare i film richiesti dall'utente e aggiungerli in un array che poi verrà stampato
    searchFilm(searchText){
      
      this.searchText = searchText;

      axios
        .get(this.apiURLFilm, {
          params: {
            api_key : 'f019de624b3557ff30c3068e6b218a54',
            query : searchText,
            language : 'it-IT'
          }
        })
        .then(response => {
          this.filmArray = response.data.results;
          console.log(this.filmArray);
        })
        .catch((error) => {
          console.log('Errore : ' + error);
        });
    },

    // funzione per cercare le serie richieste dall'utente e aggiungerle in un array che poi verrà stampato
    searchSerie(searchText){

      this.searchText = searchText;
      
      axios
        .get(this.apiURLSerie, {
          params: {
            api_key : 'f019de624b3557ff30c3068e6b218a54',
            query : searchText,
            language : 'it-IT'
          }
        })
        .then(response => {
          this.serieArray = response.data.results;
          console.log(this.serieArray);
        })
        .catch((error) => {
          console.log('Errore : ' + error);
        });
    },
    mounted() {
    // questa chiamata mostra la vista di default 
      axios
      .get('https://api.themoviedb.org/3/trending/all/week?api_key=f019de624b3557ff30c3068e6b218a54')
      .then((response) => {
        const result = response.data.results;
        this.defaultView = result;
      })            
    }
  }
}
</script>

<style lang="scss">
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.container{
  width: 100%;
  padding-left: 1px;
}
</style>