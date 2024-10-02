<template>
    <div>
     <p>chieu rong man hinh :{{width}}</p>
    </div>
  </template>
  
  <script setup>
  import { onMounted, onUpdated, ref } from 'vue';
 const width = ref(window.innerWidth);
  onUpdated(() => {
    width.value = window.innerWidth;
  });
  
  onMounted(() => {
    console.log("B8 mounted successfully");
    
  });
  </script>
  
  <style scoped>
  </style>
  