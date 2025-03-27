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
    <h2>Je L'ai Trouvé Pâtisserie</h2>
    <nav>
      <a href="#" class="nav-link" @click.prevent="handleClick('home')">Accueil</a>
      <a href="#" class="nav-link" @click.prevent="handleClick('products')">Produits</a>
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
</style> 