<script setup lang="ts">
import { ref } from 'vue'
import ImagePreview from './ImagePreview.vue'

interface GalleryImage {
  id: number;
  title: string;
  image: string;
  description: string;
}

const props = defineProps<{
  images: GalleryImage[]
}>()

const selectedImage = ref<GalleryImage | null>(null)

const openPreview = (image: GalleryImage) => {
  selectedImage.value = image
}

const closePreview = () => {
  selectedImage.value = null
}
</script>

<template>
  <section class="latest-works">
    <h2>Nos Dernières Réalisations</h2>
    <div class="gallery-grid">
      <div v-for="image in images.slice(0, 3)" :key="image.id" class="gallery-item" @click="openPreview(image)">
        <img :src="image.image" :alt="image.title">
        <div class="gallery-item-content">
          <h3>{{ image.title }}</h3>
          <p>{{ image.description }}</p>
        </div>
      </div>
    </div>
    <router-link to="/gallery" class="view-all">Voir Toutes Nos Réalisations</router-link>

    <ImagePreview
      v-if="selectedImage"
      :image="selectedImage.image"
      :title="selectedImage.title"
      :description="selectedImage.description"
      @close="closePreview"
    />
  </section>
</template>

<style scoped>
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
  cursor: pointer;
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

@media (max-width: 768px) {
  .latest-works {
    padding: 2rem 1rem;
  }

  .latest-works h2 {
    font-size: 2rem;
  }

  .gallery-grid {
    grid-template-columns: 1fr;
  }
}
</style> 