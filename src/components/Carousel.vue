<template>
  <div class="carousel w-full">
    <button @click="prevSlide" class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">
      Previous
    </button>
    <div class="slide-container">
      <transition name="fade" mode="out-in">
        <img :key="currentSlide" :src="images[currentSlide]" alt="Carousel Slide" class="w-full">
      </transition>
    </div>
    <button @click="nextSlide" class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">
      Next
    </button>
  </div>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue';

const currentSlide = ref(0);
const images = [
  'https://images.unsplash.com/photo-1620765971982-c5c4e1d1bd75?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1100&q=80',
  'https://images.unsplash.com/photo-1620765970846-3274335578d6?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1400&q=80',
  'https://images.unsplash.com/photo-1460648304944-4883b5cfcee5?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8M3x8c2xpZGVyfGVufDB8fDB8fHww&auto=format&fit=crop&w=500&q=60',
    'https://plus.unsplash.com/premium_photo-1681488000659-cc08a1c6363e?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8MjV8fHNsaWRlcnxlbnwwfHwwfHx8MA%3D%3D&auto=format&fit=crop&w=500&q=60',
];

const prevSlide = () => {
  currentSlide.value = (currentSlide.value - 1 + images.length) % images.length;
};

const nextSlide = () => {
  currentSlide.value = (currentSlide.value + 1) % images.length;
};

let interval;
onMounted(() => {
  interval = setInterval(nextSlide, 5000); // Auto advance every 5 seconds
});

onBeforeUnmount(() => {
  clearInterval(interval);
});
</script>

<style scoped>

</style>