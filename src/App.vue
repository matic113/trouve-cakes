<script setup lang="ts">
import { ref } from 'vue'
import Header from './components/Header.vue'
import CakeCard from './components/CakeCard.vue'
import Footer from './components/Footer.vue'
import Contact from './components/Contact.vue'

interface Cake {
  id: number;
  name: string;
  price: number;
  image: string;
  description: string;
}

const cakes = ref<Cake[]>([
  {
    id: 1,
    name: 'Gâteau au Chocolat Classique',
    price: 25,
    image: '/chocolate-cake.jpg',
    description: 'Gâteau au chocolat riche garni de ganache au chocolat'
  },
  {
    id: 2,
    name: 'Délices aux Fraises',
    price: 30,
    image: '/strawberry-cake.jpg',
    description: 'Gâteau à la vanille avec crème aux fraises fraîches'
  },
  {
    id: 3,
    name: 'Gâteau aux Carottes',
    price: 28,
    image: '/carrot-cake.jpg',
    description: 'Gâteau aux carottes traditionnel avec glaçage au fromage'
  }
])

const handleAddToCart = (cake: Cake) => {
  console.log('Added to cart:', cake)
  // TODO: Implement cart functionality
}

const currentRoute = ref('home')

const navigateTo = (route: string) => {
  currentRoute.value = route
}
</script>

<template>
  <div class="cake-shop">
    <Header @navigate="navigateTo" />
    
    <main class="main-content">
      <template v-if="currentRoute === 'home'">
        <section class="hero">
          <div class="hero-content">
            <h2>Gâteaux Frais & Délicieux</h2>
            <p>Faits avec amour, cuisinés avec passion</p>
            <button class="cta-button">Commander</button>
          </div>
          <div class="hero-image">
            <img src="/hero-cake.jpg" alt="Beau gâteau" />
          </div>
        </section>

        <section class="cakes-grid">
          <CakeCard 
            v-for="cake in cakes" 
            :key="cake.id" 
            :cake="cake"
            @add-to-cart="handleAddToCart"
          />
        </section>

        <Contact />
      </template>

      <template v-else-if="currentRoute === 'contact'">
        <Contact />
      </template>
    </main>

    <Footer @navigate="navigateTo" />
  </div>
</template>

<style scoped>
.cake-shop {
  font-family: 'Arial', sans-serif;
  min-height: 100vh;
  width: 100vw;
  display: flex;
  flex-direction: column;
  background-color: #fff;
}

.main-content {
  flex: 1;
  width: 100%;
  max-width: 1200px;
  margin: 2rem auto 0;
  padding: 0 1rem;
}

.hero {
  background-color: #fff5f8;
  text-align: center;
  padding: 4rem 2rem;
  margin-bottom: 2rem;
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 2rem;
  border-radius: 20px 20px 20px 20px;
}

.hero-content {
  flex: 1;
  text-align: left;
}

.hero-image {
  flex: 1;
  max-width: 500px;
}

.hero-image img {
  width: 100%;
  height: auto;
  border-radius: 15px;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
}

.hero h2 {
  color: #ff4d8d;
  font-size: 3rem;
  margin-bottom: 1rem;
  font-weight: 700;
}

.hero p {
  color: #4a4a4a;
  font-size: 1.2rem;
  margin-bottom: 2rem;
  line-height: 1.6;
}

.cta-button {
  background-color: #4fd1c5;
  color: white;
  padding: 1rem 2rem;
  border-radius: 30px;
  font-size: 1.1rem;
  font-weight: 600;
  border: none;
  cursor: pointer;
  transition: all 0.3s ease;
  box-shadow: 0 4px 15px rgba(79, 209, 197, 0.3);
}

.cta-button:hover {
  background-color: #38b2ac;
  transform: translateY(-2px);
  box-shadow: 0 6px 20px rgba(79, 209, 197, 0.4);
}

.cakes-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
  padding: 2rem 0;
  width: 100%;
}

@media (max-width: 768px) {
  .hero {
    flex-direction: column;
    text-align: center;
    padding: 2rem 1rem;
  }

  .hero-content {
    text-align: center;
  }

  .hero h2 {
    font-size: 2.5rem;
  }

  .hero-image {
    max-width: 100%;
  }
}
</style>
