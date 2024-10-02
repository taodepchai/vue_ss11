<template>
    <div>
      <h1>Đồng hồ: {{ time }}</h1>
    </div>
  </template>
  
  <script setup>
  import { ref, onMounted, onUnmounted } from 'vue';
  const formatTime = (date) => {
    const hours = String(date.getHours()).padStart(2, '0');
    const minutes = String(date.getMinutes()).padStart(2, '0');
    const seconds = String(date.getSeconds()).padStart(2, '0');
    return `${hours}:${minutes}:${seconds}`;
  };
  
  const time = ref(formatTime(new Date()));
  
  onMounted(() => {
    const interval = setInterval(() => {
      time.value = formatTime(new Date()); 
    }, 1000);
  
    onUnmounted(() => {
      clearInterval(interval);
    });
  });
  </script>
  
  <style scoped>
  h1 {
    font-family: Arial, sans-serif;
    color: #333;
  }
  </style>
  