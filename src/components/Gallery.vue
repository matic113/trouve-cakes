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
}>();

const selectedImage = ref<GalleryImage | null>(null)

const openPreview = (image: GalleryImage) => {
  selectedImage.value = image
}

const closePreview = () => {
  selectedImage.value = null
}
</script>

<template>
  <section class="gallery">
    <h2>Notre Galerie</h2>
    <div class="gallery-grid">
      <div v-for="image in images" :key="image.id" class="gallery-item" @click="openPreview(image)">
        <img :src="image.image" :alt="image.title">
        <div class="gallery-item-content">
          <h3>{{ image.title }}</h3>
          <p>{{ image.description }}</p>
        </div>
      </div>
    </div>

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
.gallery {
  padding: 4rem 2rem;
  background-color: #fff5f8;
  border-radius: 20px;
  margin: 2rem 0;
}

.gallery h2 {
  color: #ff4d8d;
  text-align: center;
  margin-bottom: 2rem;
  font-size: 2.5rem;
}

.gallery-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
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

@media (max-width: 768px) {
  .gallery {
    padding: 2rem 1rem;
  }
  
  .gallery h2 {
    font-size: 2rem;
  }
}
</style> 