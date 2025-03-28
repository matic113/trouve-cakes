<script setup lang="ts">
import { ref } from 'vue'
import Header from './components/Header.vue'
import Footer from './components/Footer.vue'
import Contact from './components/Contact.vue'
import Gallery from './components/Gallery.vue'
import Hero from './components/Hero.vue'
import EidBoxes from './components/EidBoxes.vue'
import LatestWorks from './components/LatestWorks.vue'
import CtaButton from './components/CtaButton.vue'

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
        <Hero @navigate="navigateTo" />
        <EidBoxes @navigate="navigateTo" />
        <LatestWorks :images="galleryImages" />

        <section class="custom-cta">
          <div class="cta-content">
            <h2>Un Gâteau Personnalisé pour Votre Enfant ?</h2>
            <p>Dites-nous ce que vous imaginez, nous le créons pour vous</p>
            <CtaButton variant="secondary" size="large" @click="navigateTo('contact')">Contactez-nous</CtaButton>
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

@media (max-width: 768px) {
  .custom-cta {
    padding: 2rem 1rem;
  }

  .custom-cta h2 {
    font-size: 2rem;
  }
}
</style>
