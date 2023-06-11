<script setup>
import { RouterLink, RouterView } from 'vue-router'
  

  
</script>

<template>
  <div class="contenedor">
    <header>
      <h1>Miami Hotels</h1>
      <nav class="ver">
        <RouterLink to="/">Inicio  </RouterLink><div>   </div>
        <RouterLink to="/search">Buscar</RouterLink>
      </nav>
  </header>
  
  <RouterView />
  <footer>
      <p>Derechos de autor &copy; 2023 Reservados al Hotel</p>
    </footer>
  </div>
  
</template>


<style scoped>
 nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}
  .contenedor {
    background-color: #fefcf4;
    margin: 0;
    padding: 0;
    font-family: Arial, sans-serif;
    height: 100%;
  }
  header {
    background-color: #70cbfd;
    text-align: center;
    color: #0869c0;
    padding: 10px;
  }
  nav{
    text-align: center;
  }
  footer {
    background-color: #333;
    color: #fff;
    padding: 20px;
    text-align: center;
  }
</style>