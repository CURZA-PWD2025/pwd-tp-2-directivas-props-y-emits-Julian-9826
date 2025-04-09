<template>
  <div class="card">
    <img v-if="pelicula.portada" :src="pelicula.portada" :alt="pelicula.titulo" class="poster" />
    <p v-else class="no-poster">🎞️ Portada no disponible</p>

    <div class="info">
      <h2>{{ pelicula.titulo }}</h2>
      <p><strong>🎬 Director:</strong> {{ pelicula.director }}</p>
      <p><strong>🎞️ Géneros:</strong> {{ pelicula.generos }}</p>
      <p><strong>📅 Año:</strong> {{ pelicula.anio }}</p>

      <p class="likes">❤️ {{ likes }} likes</p>
      <button @click="toggleLike" class="like-button">
        {{ liked ? 'Quitar Like' : 'Dar Like' }}
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CardComponent',
  props: {
    pelicula: Object
  },
  data() {
    return {
      liked: false,
      likes: this.pelicula.likes
    }
  },
  methods: {
    toggleLike() {
      this.liked = !this.liked
      this.likes += this.liked ? 1 : -1
      this.$emit('update_likes', { id: this.pelicula.id, likes: this.likes })
    }
  }
}
</script>

<style scoped>
.card {
  background-color: #ffffff;
  border-radius: 12px;
  box-shadow: 0 4px 16px rgba(0, 0, 0, 0.1);
  overflow: hidden;
  width: 100%;
  max-width: 320px;
  transition: transform 0.2s ease, box-shadow 0.2s ease;
  display: flex;
  flex-direction: column;
}

.card:hover {
  transform: translateY(-5px);
  box-shadow: 0 6px 20px rgba(0, 0, 0, 0.15);
}

.poster {
  width: 100%;
  height: 450px;
  object-fit: cover;
}

.no-poster {
  height: 450px;
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: #e5e7eb;
  font-style: italic;
  color: #6b7280;
}

.info {
  padding: 1rem;
  text-align: left;
}

h2 {
  font-size: 1.2rem;
  margin-bottom: 0.5rem;
  color: #111827;
}

p {
  margin: 0.3rem 0;
  font-size: 0.95rem;
  color: #374151;
}

.likes {
  margin-top: 0.8rem;
  font-weight: bold;
  color: #ef4444;
}

.like-button {
  margin-top: 0.5rem;
  padding: 0.5rem 1rem;
  background-color: #ef4444;
  color: white;
  border: none;
  border-radius: 6px;
  cursor: pointer;
  font-weight: bold;
  transition: background-color 0.2s ease;
}

.like-button:hover {
  background-color: #dc2626;
}
</style>
