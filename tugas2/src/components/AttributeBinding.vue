<template>
  <section class="container">
    <h2>profil saya</h2>
    <p>
     jika kamu ingin mengunjungi profil Instagram saya, silakan klik tautan di bawah ini. 
      <code>&lt;&gt;</code>
    </p>
    <a :href="url" target="_blank" rel="noopener" class="link">
      instagram
    </a>
    <button @click="copyLink" class="copy-btn">Copy Link</button>
    <transition name="fade-slide">
      <p v-if="copied" class="copy-msg">Link berhasil disalin!</p>
    </transition>
  </section>
</template>

<script setup>
import { ref } from 'vue';

const url = 'https://www.instagram.com/muhammadiqbalkurniaadjie?igsh=ejJxMXpzYWEwZ3Bn';
const copied = ref(false);

function copyLink() {
  navigator.clipboard.writeText(url).then(() => {
    copied.value = true;
    setTimeout(() => (copied.value = false), 2000);
  });
}
</script>

<style scoped>
.container {
  max-width: 480px;
  margin: 2rem auto;
  padding: 1rem 2rem;
  background: #f3f7f9;
  border-radius: 12px;
  box-shadow: 0 8px 15px rgba(0,0,0,0.1);
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  color: #222;
}

h2 {
  color: #070707;
  margin-bottom: 0.5rem;
  text-align: center;
}

p {
  font-size: 1rem;
  line-height: 1.5;
  margin-bottom: 1rem;
}

code {
  background: #e1eaff;
  padding: 0.2rem 0.4rem;
  border-radius: 4px;
  font-family: 'Source Code Pro', monospace;
  font-weight: 600;
}

.link {
  display: inline-block;
  background: #3498db;
  color: white;
  padding: 0.5rem 1.2rem;
  border-radius: 8px;
  text-decoration: none;
  font-weight: 600;
  transition: background-color 0.3s ease, transform 0.2s ease;
  margin-bottom: 0.5rem;
}

.link:hover {
  background: #00529b   ;
  transform: scale(1.05);
}

.copy-btn {
  display: inline-block;
  background: #00a86b;
  border: none;
  color: white;
  padding: 0.5rem 1.2rem;
  border-radius: 8px;
  cursor: pointer;
  font-weight: 600;
  transition: background-color 0.3s ease, transform 0.2s ease;
  margin-left: 1rem;
}

.copy-btn:hover {
  background: #007947;
  transform: scale(1.05);
}

.copy-msg {
  margin-top: 0.5rem;
  color: #28a745;
  font-weight: 600;
  text-align: center;
  font-size: 0.9rem;
}

.fade-slide-enter-active, .fade-slide-leave-active {
  transition: opacity 0.4s ease, transform 0.4s ease;
}
.fade-slide-enter-from, .fade-slide-leave-to {
  opacity: 0;
  transform: translateY(10px);
}
.fade-slide-enter-to, .fade-slide-leave-from {
  opacity: 1;
  transform: translateY(0);
}
</style>
