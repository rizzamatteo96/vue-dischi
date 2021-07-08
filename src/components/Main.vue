<template>
  <div class="container">
    ciao
  </div>
</template>


<script>
import axios from 'axios';

export default {
  name : 'Main',
  components: {
  },
  data(){
    return{
      urlApi : 'https://flynn.boolean.careers/exercises/api/array/music',
      apiElements : []
    }
  },
  methods: {
    loadApi(){
      axios
        .get(this.urlApi)
        .then(response => {
          console.log(response.data.response);
          this.apiElements = response.data.response;
          console.log(this.apiElements);
        });
    }
  },
  mounted(){
    this.loadApi();
  }
}
</script>


<style lang="scss">
  .container{
    width: 80%;
  }
</style>