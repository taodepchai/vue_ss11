<template>
  <div>
    <h1>Counter: {{ count }}</h1>
    <button @click="increment">Counter</button>
  </div>
</template>

<script setup>
import { ref,  onMounted, onUpdated } from "vue";

const count = ref(0);
const increment = () => {
  count.value += 1;
};
onUpdated(()=> {
    console.log("Dữ liệu đã thay đổi.");
  });
onMounted(() => {
  console.log("Component B2 đã được mount.");
});

</script>

<style scoped></style>
