<script setup lang="ts">
import { ref } from 'vue'
import CtaButton from './CtaButton.vue'
import ImagePreview from './ImagePreview.vue'

interface EidImage {
  src: string;
  alt: string;
}

const eidImages: EidImage[] = [
  {
    src: '/eid_box.jpg',
    alt: 'Boîte Eid ouverte'
  },
  {
    src: '/eid_box_closed.jpg',
    alt: 'Boîte Eid fermée'
  }
]

const selectedImage = ref<EidImage | null>(null)

const openPreview = (image: EidImage) => {
  selectedImage.value = image
}

const closePreview = () => {
  selectedImage.value = null
}

defineEmits(['navigate'])
</script>

<template>
  <section class="eid-boxes">
    <div class="eid-boxes-content">
      <div class="eid-boxes-text">
        <h2>Boîtes Eid Personnalisées</h2>
        <p>Des boîtes cadeaux élégantes et personnalisées pour vos proches à l'occasion de l'Aïd</p>
        <CtaButton @click="$emit('navigate', 'contact')">Commander</CtaButton>
      </div>
      <div class="eid-boxes-images">
        <img 
          v-for="image in eidImages" 
          :key="image.src"
          :src="image.src" 
          :alt="image.alt"
          @click="openPreview(image)"
        >
      </div>
    </div>

    <ImagePreview
      v-if="selectedImage"
      :image="selectedImage.src"
      :title="selectedImage.alt"
      description="Boîte Eid personnalisée avec des décorations élégantes"
      @close="closePreview"
    />
  </section>
</template>

<style scoped>
.eid-boxes {
  padding: 4rem 2rem;
  background-color: #ffffff;
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
  cursor: pointer;
}

.eid-boxes-images img:hover {
  transform: scale(1.02);
}

@media (max-width: 768px) {
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