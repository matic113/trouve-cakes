<script setup lang="ts">
import { ref } from 'vue'
import Header from './components/Header.vue'
import Footer from './components/Footer.vue'
import Contact from './components/Contact.vue'
import Gallery from './components/Gallery.vue'

const galleryImages = ref([
  {
    id: 1,
    title: 'Gâteau Superhéros',
    image: '/carrot-cake.jpg',
    description: 'Gâteau personnalisé avec le superhéros préféré de votre enfant'
  },
  {
    id: 2,
    title: 'Gâteau Princesse',
    image: '/chocolate-cake.jpg',
    description: 'Gâteau féerique avec décoration de princesse et château'
  },
  {
    id: 3,
    title: 'Gâteau Dinosaure',
    image: '/strawberry-cake.jpg',
    description: 'Gâteau jurassique avec dinosaures en sucre'
  }
])

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
            <h2>Gâteaux d'Anniversaire Magiques</h2>
            <p>Transformez l'anniversaire de votre enfant en moment inoubliable avec nos gâteaux personnalisés</p>
            <button class="cta-button">Demander un Devis</button>
          </div>
          <div class="hero-image">
            <img src="/hero-cake.jpg" alt="Gâteau d'anniversaire personnalisé" />
          </div>
        </section>

        <section class="eid-boxes">
          <div class="eid-boxes-content">
            <div class="eid-boxes-text">
              <h2>Boîtes Eid Personnalisées</h2>
              <p>Des boîtes cadeaux élégantes et personnalisées pour vos proches à l'occasion de l'Aïd</p>
              <button class="cta-button" @click="navigateTo('contact')">Commander</button>
            </div>
            <div class="eid-boxes-images">
              <img src="/eid_box.jpg" alt="Boîte Eid ouverte">
              <img src="/eid_box_closed.jpg" alt="Boîte Eid fermée">
            </div>
          </div>
        </section>

        <section class="latest-works">
          <h2>Nos Dernières Réalisations</h2>
          <div class="gallery-grid">
            <div v-for="image in galleryImages.slice(0, 3)" :key="image.id" class="gallery-item">
              <img :src="image.image" :alt="image.title">
              <div class="gallery-item-content">
                <h3>{{ image.title }}</h3>
                <p>{{ image.description }}</p>
              </div>
            </div>
          </div>
          <router-link to="/gallery" class="view-all">Voir Toutes Nos Réalisations</router-link>
        </section>

        <section class="custom-cta">
          <div class="cta-content">
            <h2>Un Gâteau Personnalisé pour Votre Enfant ?</h2>
            <p>Dites-nous ce que vous imaginez, nous le créons pour vous</p>
            <button class="cta-button" @click="navigateTo('contact')">Contactez-nous</button>
          </div>
        </section>
      </template>

      <template v-else-if="currentRoute === 'contact'">
        <Contact />
      </template>

      <template v-else-if="currentRoute === 'gallery'">
        <Gallery :images="galleryImages" />
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

.eid-boxes {
  padding: 4rem 2rem;
  background-color: #fff5f8;
  margin: 2rem 0;
  border-radius: 20px;
}

.eid-boxes-content {
  max-width: 1200px;
  margin: 0 auto;
  display: flex;
  align-items: center;
  gap: 4rem;
}

.eid-boxes-text {
  flex: 1;
  text-align: left;
}

.eid-boxes-text h2 {
  color: #ff4d8d;
  font-size: 2.5rem;
  margin-bottom: 1rem;
}

.eid-boxes-text p {
  color: #4a4a4a;
  font-size: 1.2rem;
  margin-bottom: 2rem;
  line-height: 1.6;
}

.eid-boxes-images {
  flex: 1;
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 1rem;
}

.eid-boxes-images img {
  width: 100%;
  height: 300px;
  object-fit: cover;
  border-radius: 15px;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease;
}

.eid-boxes-images img:hover {
  transform: scale(1.02);
}

.latest-works {
  padding: 4rem 2rem;
  background-color: #fff5f8;
  border-radius: 20px;
  margin: 2rem 0;
  text-align: center;
}

.latest-works h2 {
  color: #ff4d8d;
  font-size: 2.5rem;
  margin-bottom: 2rem;
}

.gallery-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 2rem;
  max-width: 1200px;
  margin: 0 auto;
}

.gallery-item {
  background: white;
  border-radius: 15px;
  overflow: hidden;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease;
}

.gallery-item:hover {
  transform: translateY(-5px);
}

.gallery-item img {
  width: 100%;
  height: 250px;
  object-fit: cover;
}

.gallery-item-content {
  padding: 1.5rem;
}

.gallery-item-content h3 {
  color: #ff4d8d;
  margin-bottom: 0.5rem;
  font-size: 1.2rem;
}

.gallery-item-content p {
  color: #4a4a4a;
  line-height: 1.6;
}

.view-all {
  display: inline-block;
  margin-top: 2rem;
  color: #4fd1c5;
  text-decoration: none;
  font-weight: 600;
  font-size: 1.1rem;
  transition: color 0.3s ease;
}

.view-all:hover {
  color: #38b2ac;
}

.custom-cta {
  background-color: #4fd1c5;
  padding: 4rem 2rem;
  border-radius: 20px;
  margin: 2rem 0;
  text-align: center;
  color: white;
}

.cta-content {
  max-width: 800px;
  margin: 0 auto;
}

.custom-cta h2 {
  font-size: 2.5rem;
  margin-bottom: 1rem;
}

.custom-cta p {
  font-size: 1.2rem;
  margin-bottom: 2rem;
  opacity: 0.9;
}

.custom-cta .cta-button {
  background-color: white;
  color: #4fd1c5;
  padding: 1rem 2.5rem;
  font-size: 1.2rem;
}

.custom-cta .cta-button:hover {
  background-color: #f8f9fa;
  color: #38b2ac;
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

  .gallery-grid {
    grid-template-columns: 1fr;
  }
  
  .latest-works h2,
  .custom-cta h2 {
    font-size: 2rem;
  }
  
  .latest-works,
  .custom-cta {
    padding: 2rem 1rem;
  }

  .eid-boxes {
    padding: 2rem 1rem;
  }

  .eid-boxes-content {
    flex-direction: column;
    gap: 2rem;
  }

  .eid-boxes-text {
    text-align: center;
  }

  .eid-boxes-text h2 {
    font-size: 2rem;
  }

  .eid-boxes-images {
    grid-template-columns: 1fr;
  }

  .eid-boxes-images img {
    height: 250px;
  }
}
</style>
