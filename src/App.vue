<script setup>
import { RouterLink, RouterView } from 'vue-router'
  

  
</script>

<template>
  <div class="ver">
    <header>
      <h1 class="col-md-6">Miami Hotels</h1>
      <nav>
        <RouterLink to="/">Inicio</RouterLink><div>   </div>
        <RouterLink to="/about">Buscar</RouterLink>
      </nav>
  </header>
  
  <RouterView />
  </div>
</template>


<style scoped>
  .ver {
    background-color: #fefcf4;
    margin: 0;
    padding: 0;
    font-family: Arial, sans-serif;
  }
  header {
    background-color: #70cbfd;
    color: #fff;
    padding: 10px;
  }
</style>