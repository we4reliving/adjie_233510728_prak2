<template>
  <AttributeBinding />
  <DeclarativeRendering />
  <FormBinding />
  <listRendering />
  <LifecycleHooks />
  <ComputedProperty />
  <Watchers />
  <ConditionalRendering />
</template>

<script setup>
import { ref } from 'vue'
import DeclarativeRendering from './components/Declarativerendering.vue'
import AttributeBinding from './components/AttributeBinding.vue'
import FormBinding from './components/FormBinding.vue'
import listRendering from './components/ListRendering.vue'
import LifecycleHooks from './components/LifecycleHooks.vue'
import ComputedProperty from './components/ComputedProperty.vue'
import Watchers from './components/Watchers.vue'
import ConditionalRendering from './components/ConditionalRendering.vue'
</script>
<style scoped></style>
