<script setup>
import { reactive, ref } from 'vue'

const counter = reactive({ count: 0 })
const message = ref('voting')

function increment() {
  counter.count++
}
</script>

<template>
  <div class="container">
    <h1>{{ message }}</h1>
    <p class="count-display">You voting: <strong>{{ counter.count }}</strong> times</p>
    <button @click="increment" class="btn">update</button>
  </div>
</template>

<style scoped>
.container {
  max-width: 500px;
  margin: 5rem auto;
  padding: 2rem;
  text-align: center;
  background: #ffffff;
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.1);
  border-radius: 16px;
  font-family: 'Segoe UI', sans-serif;
}

h1 {
  font-size: 2rem;
  color: #000000;
  margin-bottom: 1rem;
}

.count-display {
  font-size: 1.25rem;
  margin-bottom: 1.5rem;
  color: #555;
}

.btn {
  background-color: #42b983;
  color: white;
  border: none;
  padding: 0.75rem 1.5rem;
  font-size: 1rem;
  border-radius: 8px;
  cursor: pointer;
  transition: background-color 0.2s;
}

.btn:hover {
  background-color: #369b71;
}
</style>
