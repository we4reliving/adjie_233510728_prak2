<template>
  <section class="container">
    <h2>umur</h2>
    <div class="input-group">
      <input 
        v-model.number="age" 
        type="number" 
        placeholder="Masukkan umur" 
        class="input-field"
        min="0"
      />
      <button v-if="age !== 0" @click="resetAge" class="reset-btn">×</button>
    </div>
    <transition name="fade">
      <p v-if="age !== 0" :class="['message', isAdult ? 'adult' : 'minor']">
        {{ message }}
      </p>
    </transition>
  </section>
</template>

<script setup>
import { ref, watch, computed } from 'vue';

const age = ref(0);
const message = ref('');

const isAdult = computed(() => age.value >= 18);

watch(age, (newAge) => {
  if (newAge === 0) {
    message.value = '';
  } else {
    message.value = newAge >= 18 ? 'Dewasa' : 'Belum Dewasa';
  }
});

function resetAge() {
  age.value = 0;
}
</script>

<style scoped>
.container {
  max-width: 420px;
  margin: 2rem auto;
  padding: 1.5rem 2rem;
  background: #fcfcfc;
  border-radius: 12px;
  box-shadow: 0 7px 18px rgba(0,0,0,0.08);
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  color: #222;
  text-align: center;
}

h2 {
  color: #0d0d0f;
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
  appearance: textfield;
}

.input-field:focus {
  border-color: #0a0a0f;
  box-shadow: 0 0 8px rgba(17, 17, 18, 0.5);
}

input[type=number]::-webkit-inner-spin-button, 
input[type=number]::-webkit-outer-spin-button { 
  -webkit-appearance: none;
  margin: 0; 
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
  background: #b52e2a;
}

.message {
  font-weight: 700;
  font-size: 1.2rem;
  margin-top: 1rem;
  transition: color 0.3s ease;
}

.adult {
  color: #28a745; 
}

.minor {
  color: #dc3545; 
}


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
