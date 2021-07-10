<template>
  <header class="d-flex justify-content-between align-items-center">
    <!-- inizio logo -->
    <img src="../assets/img/logo.png" alt="logo spotify">
    <!-- fine logo -->

    <!-- inizio ordina in modo crescente o decrescente + selezione genere -->
    <div class="cont-sel">

      <button 
      class="mx-1 btn btn-primary" 
      :class="(!active) ? 'crescente' : 'decrescente'" 
      @click="active = !active; $emit('listOrder',active);"
      >Ordine </button>

      <select @change="setValueSrc($event)" class="p-1 mx-1" name="genre" id="genre">
        <option value="">Seleziona genere</option>
        <option v-for="(genre,i) in genreSelection" :key="i" :value="genre"> {{genre}} </option>
      </select>
    </div>
    <!-- fine ordina in modo crescente o decrescente + selezione genere -->
  </header>
</template>


<script>
export default {
  name : 'Header',
  props : ['genreSelection'],
  data(){
    return {
      active : false
    }
  },
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

    .cont-sel{
      .crescente::after{
        content: 'crescente';
      }
      .decrescente::after{
        content: 'decrescente';
      }
    }
  }
</style>