<template>
    <div>
      <h1>Current Count: {{ count }}</h1>
      <input type="text" v-model="val">
    </div>
  </template>
  
  <script setup>
  import { ref, onMounted, onUpdated } from 'vue';
  const val = ref('');
  
  onUpdated(() => {
    document.title = ` ${val.value}`;
    
  });
  
  onMounted(() => {
    console.log("b7 mounted successfully");
    
  });
  </script>
  
  <style scoped>
  </style>
  