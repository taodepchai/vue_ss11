<template>
    <div>
      <h1>Parent Component</h1>
      <h2>Age: {{ age }}</h2>
      <button @click="increaseAge">Increase Age</button>
      <B4childrent :age="age" />
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
import B4childrent from './B4Childrent.vue';
  
  
  const age = ref(1);
  
  const increaseAge = () => {
    age.value += 1;
  };
  </script>
  
  <style scoped>
  </style>
  