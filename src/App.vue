<template>
  <header>
      <h1 class="col-md-6">Reserva de Hotel</h1>
      <button>Reserva</button>
      <Cards/>
  </header>
  <div>
    <vue-datepicker v-model="selectedDates" multiple></vue-datepicker>
  </div>
</template>

<script setup>
  import Cards from './components/Cards.vue'
  import VueDatepicker from 'vue-datepicker';
</script>
<style scoped>
  .row{
    display: flex;
  }
</style>