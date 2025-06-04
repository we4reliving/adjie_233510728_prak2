<template>
  <section class="container">
    <h2>Cek nama</h2>
    <div class="input-group">
      <input 
        v-model="firstName" 
        placeholder="Nama Depan" 
        class="input-field"
      />
      <button v-if="firstName" @click="firstName = ''" class="reset-btn">×</button>
    </div>
    <div class="input-group">
      <input 
        v-model="lastName" 
        placeholder="Nama Belakang" 
        class="input-field"
      />
      <button v-if="lastName" @click="lastName = ''" class="reset-btn">×</button>
    </div>
    <transition name="fade">
      <p v-if="fullName.trim()" class="full-name">Nama Lengkap: {{ fullName }}</p>
    </transition>
  </section>
</template>

<script setup>
import { ref, computed } from 'vue';

const firstName = ref('');
const lastName = ref('');
const fullName = computed(() => `${firstName.value} ${lastName.value}`.trim());
</script>

<style scoped>
.container {
  max-width: 420px;
  margin: 2rem auto;
  padding: 1.5rem 2rem;
  background: #fafafa;
  border-radius: 12px;
  box-shadow: 0 6px 15px rgba(0,0,0,0.07);
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  color: #222;
  text-align: center;
}

h2 {
  color: #0c0e0e;
  margin-bottom: 1rem;
}

.input-group {
  position: relative;
  width: 100%;
  margin-bottom: 1rem;
}

.input-field {
  width: 100%;
  padding: 0.6rem 2.2rem 0.6rem 1rem;
  font-size: 1rem;
  border: 2px solid #ccc;
  border-radius: 8px;
  outline: none;
  transition: border-color 0.3s ease, box-shadow 0.3s ease;
}

.input-field:focus {
  border-color: #31708f;
  box-shadow: 0 0 8px rgba(49, 112, 143, 0.5);
}

.reset-btn {
  position: absolute;
  right: 8px;
  top: 50%;
  transform: translateY(-50%);
  background: #d9534f;
  border: none;
  color: white;
  font-weight: bold;
  font-size: 1.2rem;
  width: 26px;
  height: 26px;
  border-radius: 50%;
  cursor: pointer;
  transition: background-color 0.3s ease;
  line-height: 1;
  padding: 0;
}

.reset-btn:hover {
  background: #c12e2a;
}

.full-name {
  font-weight: 700;
  font-size: 1.3rem;
  color: #31708f;
  margin-top: 1rem;
}

/* Fade animation */
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
