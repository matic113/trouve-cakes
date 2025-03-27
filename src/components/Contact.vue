<script setup lang="ts">
import { ref } from 'vue'

const formData = ref({
  name: '',
  email: '',
  message: ''
})

const handleSubmit = () => {
  // TODO: Implement form submission
  console.log('Form submitted:', formData.value)
  // Reset form
  formData.value = {
    name: '',
    email: '',
    message: ''
  }
}
</script>

<template>
  <div class="contact-section">
    <h2>Contactez-nous</h2>
    <div class="contact-container">
      <div class="contact-info">
        <h3>Restons en Contact</h3>
        <p class="info-item">Des questions sur nos gâteaux ? Nous aimerions avoir de vos nouvelles !</p>
        <div class="info-item">
          <i class="fas fa-map-marker-alt"></i> 
          <p>123 Rue des Pâtisseries, Paris</p>
        </div>
        <div class="info-item">
          <i class="fas fa-phone"></i>
          <p>+33 1 23 45 67 89</p>
        </div>
        <div class="info-item">
          <i class="fas fa-envelope"></i>
          <p>info@patisseriedouce.fr</p>
        </div>
      </div>
      
      <form class="contact-form" @submit.prevent="handleSubmit">
        <div class="form-group">
          <label for="name">Nom</label>
          <input 
            type="text" 
            id="name" 
            v-model="formData.name" 
            required
            placeholder="Votre nom"
          >
        </div>
        
        <div class="form-group">
          <label for="email">Email</label>
          <input 
            type="email" 
            id="email" 
            v-model="formData.email" 
            required
            placeholder="Votre email"
          >
        </div>
        
        <div class="form-group">
          <label for="message">Message</label>
          <textarea 
            id="message" 
            v-model="formData.message" 
            required
            placeholder="Votre message"
            rows="5"
          ></textarea>
        </div>
        
        <button type="submit" class="submit-btn">Envoyer le Message</button>
      </form>
    </div>
  </div>
</template>

<style scoped>
.contact-section {
  padding: 4rem 2rem;
  background-color: #fff5f8;
  border-radius: 20px;
  margin: 2rem 0;
}

.contact-section h2 {
  color: #ff4d8d;
  text-align: center;
  margin-bottom: 2rem;
  font-size: 2.5rem;
}

.contact-container {
  display: grid;
  grid-template-columns: 1fr 2fr;
  gap: 3rem;
  max-width: 1000px;
  margin: 0 auto;
}

.contact-info {
  padding: 2rem;
  background: white;
  border-radius: 15px;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
}

.contact-info h3 {
  color: #ff4d8d;
  margin-bottom: 1rem;
}

.info-item {
  display: flex;
  align-items: center;
  margin: 1.5rem 0;
  color: #4a4a4a;
}

.info-item i {
  color: #4fd1c5;
  margin-right: 1rem;
  font-size: 1.2rem;
}

.contact-form {
  background: white;
  padding: 2rem;
  border-radius: 15px;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
}

.form-group {
  margin-bottom: 1.5rem;
}

.form-group label {
  display: block;
  margin-bottom: 0.5rem;
  color: #4a4a4a;
  font-weight: 600;
}

.form-group input,
.form-group textarea {
  width: 100%;
  padding: 0.8rem;
  border: 2px solid #e2e8f0;
  border-radius: 8px;
  font-size: 1rem;
  transition: border-color 0.3s ease;
}

.form-group input:focus,
.form-group textarea:focus {
  outline: none;
  border-color: #4fd1c5;
}

.submit-btn {
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
  width: 100%;
}

.submit-btn:hover {
  background-color: #38b2ac;
  transform: translateY(-2px);
  box-shadow: 0 6px 20px rgba(79, 209, 197, 0.4);
}

@media (max-width: 768px) {
  .contact-container {
    grid-template-columns: 1fr;
  }
  
  .contact-section {
    padding: 2rem 1rem;
  }
}
</style> 