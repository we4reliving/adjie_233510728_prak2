<template>
  <section class="container">
    <h2>sudah login</h2>
    <button @click="toggleShow" class="toggle-btn">
      {{ show ? 'Sembunyikan' : 'Tampilkan' }} 
    </button>
    <transition name="fade">
      <p v-if="show" ref="myElement" class="my-element">
        berhasil
      </p>
    </transition>
  </section>
</template>

<script setup>
import { onMounted, ref, watch } from 'vue';

const myElement = ref(null);
const show = ref(true);

onMounted(() => {
  console.log('Komponen dimount');
  if (myElement.value) {
    console.log('Isi elemen saat mount:', myElement.value.textContent);
  }
});

// Watch show untuk log saat elemen muncul/hilang
watch(show, (newVal) => {
  if (newVal && myElement.value) {
    console.log('Elemen ditampilkan:', myElement.value.textContent);
  } else {
    console.log('Elemen disembunyikan');
  }
});

function toggleShow() {
  show.value = !show.value;
}
</script>

<style scoped>
.container {
  max-width: 450px;
  margin: 2rem auto;
  padding: 1.5rem 2rem;
  background: #fefefe;
  border-radius: 12px;
  box-shadow: 0 8px 20px rgba(15, 15, 16, 0.1);
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  color: #ffffff;
  text-align: center;
}

h2 {
  color: #020202;
  margin-bottom: 1rem;
}

.my-element {
  font-size: 1.1rem;
  margin-top: 1rem;
  color: #00529b;
  padding: 0.7rem 1rem;
  border-radius: 8px;
  background-color: #ede7f6;
  box-shadow: 0 4px 10px rgba(248, 248, 255, 0.808);
}

/* Button styling */
.toggle-btn {
  background-color: #3498db;
  border: none;
  color: white;
  padding: 0.5rem 1.3rem;
  border-radius: 8px;
  cursor: pointer;
  font-weight: 600;
  transition: background-color 0.3s ease, transform 0.2s ease;
}

.toggle-btn:hover {
  background-color:#00529b;
  transform: scale(1.05);
}

.fade-enter-active, .fade-leave-active {
  transition: opacity 0.4s ease;
}
.fade-enter-from, .fade-leave-to {
  opacity: 0;
}
.fade-enter-to, .fade-leave-from {
  opacity: 1;
}
</style>
