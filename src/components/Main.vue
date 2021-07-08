<template>
  <div class="container">
    <div class="row row-cols-5">
      <div v-for="(card,i) in apiElements" :key="i" class="g-4">
        <CardDisk :cardInfo="card"/>
      </div>
    </div>
  </div>
</template>


<script>
import axios from 'axios';
import CardDisk from '@/components/CardDisk.vue';

export default {
  name : 'Main',
  components: {
    CardDisk,
  },
  data(){
    return{
      urlApi : 'https://flynn.boolean.careers/exercises/api/array/music',
      apiElements : []
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
          console.log(response.data.response);
          this.apiElements = response.data.response;
          console.log(this.apiElements);
        });
    }
  }
}
</script>


<style lang="scss">
  .container{
    color: white;
  }
</style>