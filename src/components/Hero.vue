<script setup lang="ts">
import CtaButton from './CtaButton.vue'

defineEmits(['navigate'])
</script>

<template>
  <section class="hero">
    <div class="hero-content">
      <h2>Gâteaux d'Anniversaire Magiques</h2>
      <p>Transformez l'anniversaire de votre enfant en moment inoubliable avec nos gâteaux personnalisés</p>
      <CtaButton @click="$emit('navigate', 'contact')">Demander un Devis</CtaButton>
    </div>
    <div class="hero-image">
      <img src="/hero-cake.jpg" alt="Gâteau d'anniversaire personnalisé" />
    </div>
  </section>
</template>

<style scoped>
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