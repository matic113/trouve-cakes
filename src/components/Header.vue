<script setup lang="ts">
const emit = defineEmits<{
  (e: 'navigate', route: string): void
}>();

const handleClick = (route: string) => {
  emit('navigate', route);
}
</script>

<template>
  <header class="header">
    <div class="logo-container" @click="handleClick('home')">
      <img src="/icon.png" alt="Logo Je L'ai Trouvé" class="logo">
      <h2>Je L'ai Trouvé Pâtisserie</h2>
    </div>
    <nav>
      <a href="#" class="nav-link" @click.prevent="handleClick('home')">Accueil</a>
      <a href="#" class="nav-link" @click.prevent="handleClick('gallery')">Galerie</a>
      <a href="#" class="nav-link" @click.prevent="handleClick('contact')">Contact</a>
    </nav>
  </header>
</template>

<style scoped>
.header {
  background-color: #ff4d8d;
  padding: 1rem 2rem;
  color: white;
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
  box-sizing: border-box;
  box-shadow: 0 2px 10px rgba(255, 77, 141, 0.2);
}

.logo-container {
  display: flex;
  align-items: center;
  gap: 1rem;
  cursor: pointer;
  transition: opacity 0.3s ease;
}

.logo-container:hover {
  opacity: 0.9;
}

.logo {
  width: 40px;
  height: 40px;
  object-fit: contain;
}

.nav-link {
  color: white;
  text-decoration: none;
  margin-left: 1.5rem;
  font-weight: 600;
  transition: color 0.3s ease;
  cursor: pointer;
}

.nav-link:hover {
  color: #4fd1c5;
}

@media (max-width: 768px) {
  .header {
    padding: 1rem;
  }

  .logo {
    width: 32px;
    height: 32px;
  }

  h2 {
    font-size: 1.2rem;
  }
}
</style> 