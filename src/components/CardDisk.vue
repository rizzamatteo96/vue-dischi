<template>
  <div class="cardDisk text-center">
    <img class="w-100 p-2" :src="cardInfo.poster" alt="">
    <div class="text-uppercase fs-3 fw-bolder mb-3"> {{cardInfo.title}} </div>
    <div class="text-secondary"> {{cardInfo.author}} </div>
    <div class="text-secondary mb-3"> {{cardInfo.year}} </div>
  </div>
</template>

<script>
export default {
  name : 'CardDisk',
  props : ["cardInfo"]
}
</script>

<style lang="scss">
  .cardDisk{
    background-color: #2e3a46;
    height: 100%;
  }
</style>




// {
//   "poster": "https://www.onstageweb.com/wp-content/uploads/2018/09/bon-jovi-new-jersey.jpg",
//   "title": "New Jersey",
//   "author": "Bon Jovi",
//   "genre": "Rock",
//   "year": "1988"
// },