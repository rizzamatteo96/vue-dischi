<template>
  <div class="loading text-center position-absolute top-50 start-50 translate-middle">
    <img src="../assets/img/logo.png" alt="logo spotify">
    <div class="mt-3 text-uppercase fs-1 fw-bolder text-white">...Loading...</div>
  </div>
</template>


<script>
export default {
  name : 'LoadingPage'
}
</script>


<style lang="scss">
  .loading{
    img{
      height: 100px;
      animation: loading 1s infinite;
    }
  
    @keyframes loading {
      from{
        transform: rotate(0);
      }
  
      to{
        transform: rotate(360deg);
      }
    }
  }
</style>