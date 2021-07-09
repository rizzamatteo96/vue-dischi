<template>
  <div id="app">
    <Header/>
    <Main v-if="!dataLoading" :cardData="apiElements"/>
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
        });
    }
  }
}
</script>

<style lang="scss">
  @import '@/style/commons.scss';
</style>
