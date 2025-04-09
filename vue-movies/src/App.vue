<template>
  <div>
    <h1>Listado de Películas</h1>
    <div class="peliculas">
      <CardComponent v-for="p in peliculas" :key="p.id" :pelicula="p" />
    </div>
  </div>
</template>

<script>
import peliculas from './resource/movies.ts'
import CardComponent from './components/CardComponent.vue'

export default {
  components: {
    CardComponent
  },
  data() {
    return {
      peliculas
    }
  }
}
</script>

<style>
body {
  font-family: Arial, sans-serif;
  background-color: #eee;
  margin: 0;
  padding: 0;
}
h1 {
  text-align: center;
  padding: 2rem 1rem 1rem;
  font-size: 2rem;
  color: #1f2937;
}
.peliculas {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 2rem;
  padding: 2rem;
  max-width: 1200px;
  margin: 0 auto;
}

</style>

 
