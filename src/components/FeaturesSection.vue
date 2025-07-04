<template>
  <section id="features"
    class="relative min-h-screen w-full bg-cover bg-center py-8 text-white md:flex items-center overflow-x-hidden "
    :style="{ backgroundImage: `url(${featuresBg})` }" style="touch-action: manipulation;">
    <div class="absolute inset-0 bg-[#2F1893] opacity-50 z-0"></div>
    <div class="z-10 relative flex flex-col lg:flex-row items-center justify-start gap-10 w-full">
      <!-- laptop  -->
      <div class="hidden lg:flex flex-[0.4] sticky top-20 justify-start">
        <img src="/src/assets/images/features_laptop.svg" class="w-full mx-auto h-[200px] md:h-[400px] lg:h-[535px]" />
      </div>

      <!-- content -->
      <div class="w-full relative overflow-hidden mt-16 px-4 lg:flex-[0.5]">
        <div class="flex transition-transform duration-500 ease-in-out"
          :style="{ transform: `translateX(-${currentSlide * 100}%)` }">
          <div v-for="(slide, index) in slides" :key="index"
            class="w-full shrink-0 px-4 sm:px-6 space-y-14 md:space-y-12">
            <div class="space-y-6">
              <h3 class="text-3xl md:text-4xl lg:text-[42px] font-bold tracking-[-0.4px]">
                {{ slide.title }}
              </h3>
              <p class="text-lg md:text-[22px] font-medium">
                {{ slide.description }}
              </p>
            </div>
            <!-- features  -->
            <div class="grid grid-cols-1 md:grid-cols-2 mt-12 space-y-8 md:space-y-0 md:gap-12">
              <div v-for="(feature, i) in slide.features" :key="i" class="space-y-4">
                <component :is="feature.icon" class="w-[37.6px] h-[37.6px]" />
                <h3 class="text-base font-bold tracking-[2px] uppercase">
                  {{ feature.title }}
                </h3>
                <p class="font-sans font-normal text-base">
                  {{ feature.description }}
                </p>
              </div>
            </div>
          </div>
        </div>
      </div>

      <!-- dots-->
      <div class="mt-10 flex items-center justify-center space-x-3 lg:rotate-90">
        <button v-for="(slide, index) in slides" :key="index" @click="goToSlide(index)" :class="[
          'w-3 h-3 rounded-full transition-all duration-300',
          currentSlide === index
            ? 'bg-white'
            : 'bg-transparent border-2 opacity-30 hover:bg-white hover:opacity-100',
        ]" />
      </div>
    </div>
  </section>
</template>

<script setup>
import featuresBg from "@/assets/images/features_bg.jpg";
import {
  Copy,
  Gem,
  Handshake,
  Puzzle,
  Expand,
  GlobeLock,
  ArrowDownUp,
  Palette,
} from "lucide-vue-next";
import { ref, onMounted, onBeforeUnmount } from "vue";

const slides = [
  {
    id: 1,
    title: "We Create Something New",
    description:
      "We have created a new product that will help designers, developers and companies create websites for their startups quickly and easily.",
    features: [
      {
        icon: Copy,
        title: "30 NEW FEATURE PAGES",
        description:
          "Startup Framework contains components and complex blocks which can easily",
      },
      {
        icon: Gem,
        title: "USEFUL SYMBOL COMPONENTS",
        description:
          "Samples will show you the feeling on how to play around using the components",
      },
    ],
  },
  {
    id: 2,
    title: "Powerful Tools for Teams",
    description:
      "Empower your team to collaborate and launch projects with ease. Our platform is designed to streamline workflows and enhance productivity.",
    features: [
      {
        icon: Handshake,
        title: "TEAM COLLABORATION",
        description:
          "Assign roles, track progress, and share feedback in one unified environment.",
      },
      {
        icon: Puzzle,
        title: "CROSS-PLATFORM ACCESS",
        description:
          "Access your projects from any device with full responsiveness and sync.",
      },
    ],
  },
  {
    id: 3,
    title: "Design with Precision",
    description:
      "Build beautiful layouts in minutes. Our tools allow you to rapidly prototype and fine-tune your product design with high accuracy.",
    features: [
      {
        icon: Palette,
        title: "PIXEL PERFECT DESIGN",
        description:
          "Every block and component is optimized for consistency and alignment.",
      },
      {
        icon: ArrowDownUp,
        title: "EFFICIENT WORKFLOW",
        description:
          "Speed up your design process with smart components and reusable patterns.",
      },
    ],
  },
  {
    id: 4,
    title: "Launch and Scale",
    description:
      "From MVP to full-scale product, our framework scales with your growth. Ship faster and maintain quality at every stage.",
    features: [
      {
        icon: GlobeLock,
        title: "READY FOR PRODUCTION",
        description:
          "All blocks are tested, responsive, and ready to go live without heavy modifications.",
      },
      {
        icon: Expand,
        title: "BUILT TO SCALE",
        description:
          "Easily extend your project with scalable components and consistent design logic.",
      },
    ],
  },
];

let intervalId;

const currentSlide = ref(0);

const goToSlide = (index) => {
  currentSlide.value = index;
};

const nextSlide = () => {
  currentSlide.value = (currentSlide.value + 1) % slides.length;
};

onMounted(() => {
  intervalId = setInterval(nextSlide, 5000);
});

onBeforeUnmount(() => {
  clearInterval(intervalId);
});
</script>
