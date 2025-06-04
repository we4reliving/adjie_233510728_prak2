<template>
  <section class="container">
    <h2>data saya</h2>
    <transition-group name="fade-slide" tag="ul" class="item-list">
      <li 
        v-for="(item, index) in items" 
        :key="index" 
        class="item"
      >
        {{ item }}
      </li>
    </transition-group>
  </section>
</template>

<script setup>
const items = ['Nama', 'Npm', 'jurusan', 'fakultas', 'alamat', 'no hp'];    
</script>

<style scoped>
.container {    
  max-width: 400px;
  margin: 2rem auto;
  padding: 1.5rem 2rem;
  background: hsl(0, 100%, 99%);
  border-radius: 12px;
  box-shadow: 0 8px 20px rgba(0,0,0,0.1);
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  color: #ffffff;
  text-align: center;
}

h2 {
  color: #070707;
  margin-bottom: 1rem;
}

.item-list {
  list-style-type: none;
  padding: 0;
  margin: 0;
}

.item {
  background: #3498db;
  color: rgb(240, 240, 240);
  padding: 0.8rem 1rem;
  margin-bottom: 0.6rem;
  border-radius: 8px;
  cursor: default;
  font-weight: 600;
  box-shadow: 0 4px 8px rgba(12, 12, 12, 0.4);
  transition: background-color 0.3s ease, transform 0.3s ease;
}

.item:hover {
  background: #00529b;
  transform: translateX(8px);
}

.fade-slide-enter-active, .fade-slide-leave-active {
  transition: opacity 0.4s ease, transform 0.4s ease;
}

.fade-slide-enter-from, .fade-slide-leave-to {
  opacity: 0;
  transform: translateX(-15px);
}

.fade-slide-enter-to, .fade-slide-leave-from {
  opacity: 1;
  transform: translateX(0);
}
</style>
