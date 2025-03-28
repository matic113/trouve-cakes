<script setup lang="ts">
interface Props {
  variant?: 'primary' | 'secondary'
  size?: 'normal' | 'large'
}

withDefaults(defineProps<Props>(), {
  variant: 'primary',
  size: 'normal'
})
</script>

<template>
  <button 
    class="cta-button" 
    :class="[`cta-button--${variant}`, `cta-button--${size}`]"
    @click="$emit('click')"
  >
    <slot></slot>
  </button>
</template>

<style scoped>
.cta-button {
  border-radius: 30px;
  font-size: 1.1rem;
  font-weight: 600;
  border: none;
  cursor: pointer;
  transition: all 0.3s ease;
}

.cta-button--primary {
  background-color: #4fd1c5;
  color: white;
  padding: 1rem 2rem;
  box-shadow: 0 4px 15px rgba(79, 209, 197, 0.3);
}

.cta-button--primary:hover {
  background-color: #38b2ac;
  transform: translateY(-2px);
  box-shadow: 0 6px 20px rgba(79, 209, 197, 0.4);
}

.cta-button--secondary {
  background-color: white;
  color: #4fd1c5;
  padding: 1rem 2rem;
  box-shadow: 0 4px 15px rgba(255, 255, 255, 0.3);
}

.cta-button--secondary:hover {
  background-color: #f8f9fa;
  color: #38b2ac;
  transform: translateY(-2px);
  box-shadow: 0 6px 20px rgba(255, 255, 255, 0.4);
}

.cta-button--large {
  padding: 1rem 2.5rem;
  font-size: 1.2rem;
}
</style> 