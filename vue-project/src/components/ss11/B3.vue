<template>
    <div>
      <h1>Age: {{ age }}</h1>
      <h2>Company: {{ currentCompany }}</h2>
      <button @click="updateAge">Random</button>
    </div>
  </template>
  
  <script setup>
  import { ref, onMounted, onUpdated } from 'vue';
  const age = ref(1);
  const companies = ["Rikkei Academy", "Rikkei Education", "Rikkei Fukuoka"];
  const currentCompany = ref(companies[0]);
  const updateAge = () => {
    age.value = Math.floor(Math.random() * 3) + 1; 
  };
  
  onUpdated(() => {
    currentCompany.value = companies[age.value - 1]; 
    console.log('Dữ liệu đã thay đổi: ', age.value);
  });
  
  onMounted(() => {
    console.log('Component B3 đã được mount.');
  });
  </script>
  
