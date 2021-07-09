<template>
  <div class="container">
    <div class="row row-cols-5">
      <div v-for="(card,i) in cardData" :key="i" class="g-4">
        <CardDisk :cardInfo="card"/>
      </div>
    </div>

  </div>
</template>


<script>
import CardDisk from '@/components/CardDisk.vue';

export default {
  name : 'Main',
  props : ['cardData', 'genreToShow'],
  components: {
    CardDisk
  }
}
</script>


<style lang="scss">
  .container{
    color: white;
  }
</style>