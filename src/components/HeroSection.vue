<template>
  <section id="home" class="min-h-screen bg-cover bg-center flex items-center justify-center text-white"
    :style="{ backgroundImage: `url(${herobg})` }" style="touch-action: manipulation;">
    <div class="absolute inset-0 bg-[#2F1893] opacity-50 z-0"></div>
    <div class="relative z-10 flex flex-col items-center justify-center text-center h-full overflow-hidden">
        <!-- <HeroCarousel /> -->
      <!-- cta button -->
      <BaseButton href="#cta" class="bg-[#482BE7] hover:bg-blue-700 h-[60px] px-9 text-[18px] mt-8"
        text="Create an Account" />
    </div>
  </section>
</template>

<script setup>
import herobg from "@/assets/images/hero.jpg";
// import HeroCarousel from "./HeroCarousel.vue";
import BaseButton from "./BaseButton.vue";
</script>
