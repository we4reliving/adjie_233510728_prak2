<template>
  <section class="card">
    <h2 class="title">pesan yang tersimpan</h2>

    <button @click="show = !show" class="toggle-btn">
      {{ show ? 'Sembunyikan' : 'Tampilkan' }} Pesan
    </button>

    <p v-if="show" class="message">
      Teruslah belajar dan tingkatkan skill anda <code>semangat!!</code>.
    </p>
  </section>
</template>

<script setup>
import { ref } from 'vue';
const show = ref(true);
</script>

<style scoped>
.card {
  max-width: 500px;
  margin: 3rem auto;
  padding: 2rem;
  background-color: #fff;
  border-radius: 16px;
  box-shadow: 0 6px 16px rgba(0, 0, 0, 0.1);
  text-align: center;
  font-family: Arial, sans-serif;
}

.title {
  font-size: 1.8rem;
  margin-bottom: 1.2rem;
  color: #070a0c;
}

.toggle-btn {
  background-color: #3498db;
  color: white;
  padding: 0.6rem 1.2rem;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  transition: background-color 0.3s;
  margin-bottom: 1rem;
}

.toggle-btn:hover {
  background-color: #00529b;
}

.message {
  font-size: 1rem;
  color: #333;
  background-color: #ecf0f1;
  padding: 0.8rem;
  border-radius: 8px;
}
</style>
