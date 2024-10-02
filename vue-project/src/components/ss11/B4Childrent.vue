<template>
    <div>
      <h2>Child Component</h2>
      <p>Received Age: {{ age }}</p>
    </div>
  </template>
  
  <script setup>
  import { defineProps,  onMounted, onUpdated } from 'vue';
  const props = defineProps({
    age: {
      type: Number,
      required: true
    }
  });
  onUpdated(()=>{
    alert ("gia tri bien age thay doi")
  }
)
  onMounted(() => {
    console.log('Component Ex04Children đã được mount.');
  });
  </script>
  
  <style scoped>
  </style>
  