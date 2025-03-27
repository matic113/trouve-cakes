<script setup lang="ts">
interface Cake {
  id: number;
  name: string;
  price: number;
  image: string;
  description: string;
  customization: string[];
  category: 'wedding' | 'children';
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
    <div class="category-badge">
      Anniversaire
    </div>
    <img :src="cake.image" :alt="cake.name" class="cake-image">
    <div class="cake-content">
      <h3>{{ cake.name }}</h3>
      <p class="description">{{ cake.description }}</p>
      <div class="customization-options">
        <h4>Options de Personnalisation:</h4>
        <ul>
          <li v-for="option in cake.customization" :key="option">{{ option }}</li>
        </ul>
      </div>
      <p class="price">{{ cake.price }}€</p>
      <button class="order-btn" @click="emit('addToCart', cake)">Demander un Devis</button>
    </div>
  </div>
</template>

<style scoped>
.cake-card {
  background: white;
  border-radius: 15px;
  box-shadow: 0 4px 15px rgba(0,0,0,0.1);
  padding: 1.5rem;
  text-align: center;
  transition: transform 0.3s ease;
  display: flex;
  flex-direction: column;
  height: 100%;
  position: relative;
  min-height: 600px;
}

.category-badge {
  position: absolute;
  top: 1.5rem;
  right: 1.5rem;
  padding: 0.8rem 1.5rem;
  border-radius: 25px;
  color: white;
  font-weight: 600;
  font-size: 1.1rem;
  background-color: #4fd1c5;
  z-index: 1;
  box-shadow: 0 2px 8px rgba(79, 209, 197, 0.3);
}

.cake-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 25px rgba(0,0,0,0.15);
}

.cake-image {
  width: 100%;
  height: 300px;
  object-fit: cover;
  border-radius: 12px;
  margin-bottom: 1.5rem;
  box-shadow: 0 4px 12px rgba(0,0,0,0.1);
}

.cake-content {
  display: flex;
  flex-direction: column;
  flex: 1;
  justify-content: space-between;
  padding: 0 0.5rem;
}

.cake-content h3 {
  color: #ff4d8d;
  font-size: 1.8rem;
  margin-bottom: 1rem;
  font-weight: 700;
}

.description {
  color: #4a4a4a;
  margin: 1rem 0;
  flex: 1;
  font-size: 1.1rem;
  line-height: 1.6;
}

.customization-options {
  text-align: left;
  margin: 1.5rem 0;
  padding: 1.5rem;
  background-color: #f8f9fa;
  border-radius: 12px;
}

.customization-options h4 {
  color: #ff4d8d;
  margin-bottom: 1rem;
  font-size: 1.2rem;
  font-weight: 600;
}

.customization-options ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.customization-options li {
  color: #4a4a4a;
  margin: 0.5rem 0;
  font-size: 1.1rem;
  padding-left: 1.5rem;
  position: relative;
}

.customization-options li::before {
  content: "•";
  color: #4fd1c5;
  position: absolute;
  left: 0;
}

.price {
  color: #ff4d8d;
  font-weight: bold;
  font-size: 1.5rem;
  margin: 1.5rem 0;
}

.order-btn {
  background-color: #4fd1c5;
  color: white;
  border: none;
  padding: 1rem 2rem;
  border-radius: 30px;
  font-size: 1.2rem;
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

@media (max-width: 768px) {
  .cake-card {
    min-height: 500px;
  }
  
  .cake-image {
    height: 250px;
  }
  
  .cake-content h3 {
    font-size: 1.5rem;
  }
}
</style> 