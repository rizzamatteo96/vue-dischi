<template>
  <div id="app">
    <Header :genreSelection="genreArray" @searchVal="filterGenre"/>
    <Main v-if="!dataLoading" :cardData="filteredArray"/>
    <LoadingPage v-else/>
  </div>
</template>

<script>
import axios from 'axios';
import Header from './components/Header.vue';
import Main from './components/Main.vue';
import LoadingPage from '@/components/LoadingPage.vue';

export default {
  name: 'App',
  components: {
    Header,
    Main,
    LoadingPage
  },
  data(){
    return{
      urlApi : 'https://flynn.boolean.careers/exercises/api/array/music',
      apiElements : [],
      genreArray : [],
      filteredArray : [],
      dataLoading : true
    }
  },
  created(){
    this.loadApi();
  },
  methods: {
    loadApi(){
      axios
        .get(this.urlApi)
        .then(response => {
          // console.log(response.data.response);
          this.apiElements = response.data.response;
          // console.log(this.apiElements);
          this.dataLoading = false;
          this.loadGenre();
          this.filterGenre();
        })
        .catch(err => {
          console.log('Errore: ' + err);
        });
    },
    loadGenre(){
      // funzione che estrapola tutti i generi musicali presenti nella api per la selezione
      this.apiElements.forEach((element) => {
        if(!this.genreArray.includes(element.genre)){
          this.genreArray.push(element.genre);
        }
      });
      // console.log(this.genreArray);
    },
    filterGenre(inputFormHeader){
      this.filteredArray = this.apiElements.filter((element) => {
        if(!inputFormHeader){
          return this.apiElements;
        }
        else{
          return element.genre.includes(inputFormHeader);
        }
      });
      // console.log(inputFormHeader);
      // console.log(this.filteredArray);
    }
  }
}
</script>

<style lang="scss">
  @import '@/style/commons.scss';
</style>
