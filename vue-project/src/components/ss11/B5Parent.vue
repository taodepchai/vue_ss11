<template>
    <div>
      <h1>Parent Component</h1>
      <button @click="toggleChildren">{{ showChildren ? 'Hide' : 'Show' }} Child</button>
      <B5Childrent v-if="showChildren" @unmount="handleUnmount" />
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
import B5Childrent from './B5Childrent.vue';

  
  const showChildren = ref(false);
  
  const toggleChildren = () => {
    showChildren.value = !showChildren.value;
  };
  
  const handleUnmount = () => {
    console.log('beforeUnmount: Component is about to be unmounted');
    console.log('unmounted: Component has been unmounted');
  };
  </script>
  
  <style scoped>
  </style>
  