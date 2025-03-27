<script setup lang="ts">
interface Cake {
  id: number;
  name: string;
  price: number;
  image: string;
  description: string;
}

defineProps<{
  cake: Cake
}>();

const emit = defineEmits<{
  (e: 'addToCart', cake: Cake): void
}>();
</script>

<template>
  <div class="cake-card">
    <img :src="cake.image" :alt="cake.name" class="cake-image">
    <div class="cake-content">
      <h3>{{ cake.name }}</h3>
      <p class="description">{{ cake.description }}</p>
      <p class="price">{{ cake.price }}€</p>
      <button class="order-btn" @click="emit('addToCart', cake)">Ajouter au Panier</button>
    </div>
  </div>
</template>

<style scoped>
.cake-card {
  background: white;
  border-radius: 10px;
  box-shadow: 0 2px 8px rgba(0,0,0,0.1);
  padding: 1rem;
  text-align: center;
  transition: transform 0.3s ease;
  display: flex;
  flex-direction: column;
  height: 100%;
}

.cake-card:hover {
  transform: translateY(-5px);
}

.cake-image {
  width: 100%;
  height: 200px;
  object-fit: cover;
  border-radius: 8px;
  margin-bottom: 1rem;
}

.cake-content {
  display: flex;
  flex-direction: column;
  flex: 1;
  justify-content: space-between;
}

.description {
  color: #666;
  margin: 1rem 0;
  flex: 1;
}

.price {
  color: #ff4d8d;
  font-weight: bold;
  font-size: 1.2rem;
  margin: 1rem 0;
}

.order-btn {
  background-color: #4fd1c5;
  color: white;
  border: none;
  padding: 0.8rem 1.5rem;
  border-radius: 30px;
  font-size: 1rem;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s ease;
  box-shadow: 0 4px 15px rgba(79, 209, 197, 0.3);
  width: 100%;
  margin-top: auto;
}

.order-btn:hover {
  background-color: #38b2ac;
  transform: translateY(-2px);
  box-shadow: 0 6px 20px rgba(79, 209, 197, 0.4);
}
</style> 