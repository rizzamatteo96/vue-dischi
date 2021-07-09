<template>
  <header class="d-flex justify-content-between align-items-center">
    <img src="../assets/img/logo.png" alt="logo spotify">

    <div class="cont-sel">
      <select @change="setValueSrc($event)" class="p-1" name="genre" id="genre">
        <option value="">Seleziona genere</option>
        <option v-for="(genre,i) in genreSelection" :key="i" :value="genre"> {{genre}} </option>
      </select>
    </div>
  </header>
</template>


<script>
export default {
  name : 'Header',
  props : ['genreSelection'],
  methods : {
    setValueSrc(event){
      // console.log(event.target.value);
      this.$emit('searchVal', event.target.value);
    }
  }
}
</script>


<style lang="scss">
  header{
    background-color: #2e3a46;
    height: 100px;
    padding: 10px 20px;

    img{
      height: 80px;
    }
  }
</style>