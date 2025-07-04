<template>
  <section
    class="min-h-screen bg-cover bg-center flex items-center justify-center text-white"
    :style="{ backgroundImage: `url(${herobg})` }"
  >
    <div class="absolute inset-0 bg-[#2F1893] opacity-50 z-0"></div>

    <AppNavbar class="z-30" />

    <div class="z-20">
      <HeroCarousel />
    </div>
  </section>
</template>

<script setup>
import AppNavbar from './AppNavbar.vue'
import herobg from '@/assets/images/hero.jpg'
import HeroCarousel from './HeroCarousel.vue'
</script>
