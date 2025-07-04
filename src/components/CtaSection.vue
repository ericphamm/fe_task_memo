<template>
  <section
    id="cta"
    class="relative min-h-screen w-full bg-cover bg-center text-white md:flex items-center justify-center overflow-x-hidden"
    style="background-image: url('/src/assets/images/CTA_bg.jpg')"
  >
    <div class="absolute inset-0 bg-[#2F1893] opacity-30 z-0"></div>

    <div class="relative z-10 flex flex-col items-center justify-center text-center h-full min-h-screen px-16 space-y-14">
      <h2 class="text-white leading-[70px] text-5xl lg:text-[58px] font-bold break-words tracking-[-0.025em] text-center">
          Easy to setup.<br />
  Easy to maintain
</h2>

<div class="w-[60%]">
<p class="text-base md:text-[22px] sm:text-lg font-medium text-center leading-relaxed max-w-2xl md:max-w-3xl lg:max-w-4xl mx-auto">
  
  Bootstrap is a widely-used, sleek, intuitive and powerful front-end framework for faster and easier web development.</p>
</div>

  <div class="flex items-center justify-center gap-8">
  <a
  href="#contact"
  class="bg-[#EA3223] hover:bg-[#e85447] w-[70px] h-[70px] rounded-full flex items-center justify-center transition-all duration-300 transform hover:scale-105"
>
      <font-awesome-icon :icon="['fas', 'play']" class="text-white text-xl"/>
        </a>
<BaseButton href="#contact" class="bg-[#25DAC5] hover:bg-[#00e69a]" text="Get Started" />

</div>

</div>

   
  </section>
</template>
<script setup>
import BaseButton from './BaseButton.vue';
</script>
