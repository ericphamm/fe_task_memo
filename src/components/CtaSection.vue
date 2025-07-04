<template>
  <section id="cta"
    class="relative min-h-screen w-full bg-cover bg-center text-white md:flex items-center justify-center overflow-x-hidden"
    :style="{ backgroundImage: `url(${ctaBg})` }" style="touch-action: manipulation;">
    <div class="absolute inset-0 bg-[#2F1893] opacity-30 z-0"></div>
    <div
      class="relative z-10 flex flex-col items-center justify-center text-center h-full min-h-screen px-6 md:px-16 space-y-14">
      <h2
        class="text-white text-5xl lg:text-[58px] leading-[70px] font-bold break-words tracking-[-0.025em] text-center">
        Easy to setup.<br />
        Easy to maintain
      </h2>
      <div class="w-[60%]">
        <p class="text-lg md:text-[22px] font-medium text-center max-w-2xl md:max-w-3xl lg:max-w-4xl mx-auto">
          Bootstrap is a widely-used, sleek, intuitive and powerful front-end
          framework for faster and easier web development.
        </p>
      </div>
      <div class="flex items-center justify-center gap-3 sm:gap-8">
        <a href="#contact"
          class="bg-[#EA3223] hover:bg-[#e85447] w-[70px] h-[70px] rounded-full flex items-center justify-center transition-all duration-300 transform hover:scale-105">
          <font-awesome-icon :icon="['fas', 'play']" class="text-white text-xl" />
        </a>
        <BaseButton href="#contact" class="bg-[#25DAC5] hover:bg-[#00e69a] h-[70px] px-6 md:px-14" text="Get Started" />
      </div>
    </div>
  </section>
</template>

<script setup>
import ctaBg from "@/assets/images/CTA_bg.jpg";
import BaseButton from "./BaseButton.vue";
</script>
