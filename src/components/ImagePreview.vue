<script setup lang="ts">
interface Props {
  image: string;
  title: string;
  description: string;
}

defineProps<Props>();
defineEmits<{
  (e: 'close'): void;
}>();
</script>

<template>
  <div class="image-preview-overlay" @click="$emit('close')">
    <div class="image-preview-content" @click.stop>
      <button class="close-button" @click="$emit('close')">&times;</button>
      <img :src="image" :alt="title" class="preview-image">
      <div class="preview-info">
        <h3>{{ title }}</h3>
        <p>{{ description }}</p>
      </div>
    </div>
  </div>
</template>

<style scoped>
.image-preview-overlay {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(0, 0, 0, 0.8);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 1000;
  cursor: pointer;
}

.image-preview-content {
  position: relative;
  max-width: 90vw;
  max-height: 90vh;
  background: white;
  border-radius: 15px;
  overflow: hidden;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.3);
}

.close-button {
  position: absolute;
  top: 1rem;
  right: 1rem;
  background: rgba(0, 0, 0, 0.5);
  color: white;
  border: none;
  width: 40px;
  height: 40px;
  border-radius: 50%;
  font-size: 24px;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: background-color 0.3s ease;
}

.close-button:hover {
  background: rgba(0, 0, 0, 0.8);
}

.preview-image {
  width: 100%;
  height: auto;
  max-height: 80vh;
  object-fit: contain;
}

.preview-info {
  padding: 1.5rem;
  background: white;
}

.preview-info h3 {
  color: #ff4d8d;
  margin-bottom: 0.5rem;
  font-size: 1.5rem;
}

.preview-info p {
  color: #4a4a4a;
  line-height: 1.6;
}

@media (max-width: 768px) {
  .image-preview-content {
    max-width: 95vw;
    max-height: 95vh;
  }

  .preview-info {
    padding: 1rem;
  }

  .preview-info h3 {
    font-size: 1.2rem;
  }
}
</style> 