<template>
  <section class="container">
    <h2>Yang terkait</h2>
    <input 
      v-model="name" 
      placeholder="Masukkan nama" 
      class="input-name"
      @focus="focused = true"
      @blur="focused = false"
    />
    <button v-if="name" @click="resetName" class="reset-btn">Reset</button>
    <transition name="fade">
      <p v-if="name" class="greeting">Halo, {{ name }} 👋</p>
    </transition>
  </section>
</template>

<script setup>
import { ref } from 'vue';

const name = ref('');
const focused = ref(false);

function resetName() {
  name.value = '';
}
</script>

<style scoped>
.container {
  max-width: 420px;
  margin: 2rem auto;
  padding: 1.5rem 2rem;
  background: #f9fafb;
  border-radius: 12px;
  box-shadow: 0 6px 12px rgba(0,0,0,0.08);
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  color: #222;
  text-align: center;
}

h2 {
  color: #0c0d0e;
  margin-bottom: 1rem;
}

.input-name {
  width: 70%;
  padding: 0.6rem 0.9rem;
  font-size: 1rem;
  border: 2px solid #ccc;
  border-radius: 8px;
  transition: border-color 0.3s ease, box-shadow 0.3s ease;
  outline: none;
}

.input-name:focus {
  border-color: #0077cc;
  box-shadow: 0 0 8px rgba(0,119,204,0.4);
}

.reset-btn {
  margin-left: 1rem;
  background: #cc0000;
  border: none;
  color: white;
  padding: 0.5rem 1rem;
  border-radius: 8px;
  cursor: pointer;
  font-weight: 600;
  transition: background-color 0.3s ease, transform 0.2s ease;
}

.reset-btn:hover {
  background: #990000;
  transform: scale(1.05);
}

.greeting {
  margin-top: 1.2rem;
  font-size: 1.25rem;
  font-weight: 700;
  color: #0077cc;
}

/* Animasi fade sederhana */
.fade-enter-active, .fade-leave-active {
  transition: opacity 0.5s ease;
}
.fade-enter-from, .fade-leave-to {
  opacity: 0;
}
.fade-enter-to, .fade-leave-from {
  opacity: 1;
}
</style>
