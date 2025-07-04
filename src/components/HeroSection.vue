<template>
  <section id="home"
    class="min-h-screen bg-cover bg-center flex items-center justify-center text-white"
    :style="{ backgroundImage: `url(${herobg})` }"
  >
    <div class="absolute inset-0 bg-[#2F1893] opacity-50 z-0"></div>

 
    <div>
      <HeroCarousel />
    </div>
  </section>
</template>

<script setup>
import herobg from '@/assets/images/hero.jpg'
import HeroCarousel from './HeroCarousel.vue'
</script>
