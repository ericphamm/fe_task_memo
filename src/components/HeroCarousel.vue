<template>
  <div class="relative w-full min-h-[400px] flex items-center justify-center px-4 text-white overflow-hidden" style="touch-action: manipulation;">

    <div class="flex items-center justify-between w-full max-w-7xl mx-auto overflow-x-hidden">
      <!-- prev arrow -->
      <button @click="prevSlide"
        class="p-3 rounded-full bg-transparent transition-all duration-300 transform hover:scale-125 z-10 flex-shrink-0">
        <MdNavigateNext class="w-9 h-9 rotate-180" />
      </button>
      <!-- slides -->
      <div class="flex flex-col mx-auto items-center space-y-14 px-2 py-4 flex-grow overflow-x-hidden">
        <div class="flex transition-transform duration-700 ease-in-out w-full"
          :style="{ transform: `translateX(-${currentIndex * 100}%)` }">
          <div v-for="(slide, index) in slides" :key="index" class="w-full flex-shrink-0 text-center space-y-6">
            <p class="text-2xl font-bold">{{ slide.littleTitle }}</p>
            <h1 class="text-3xl sm:text-4xl md:text-5xl lg:text-6xl font-bold leading-tight break-words px-2">
              {{ slide.mainTitle }}
            </h1>
            <div class="w-full sm:w-[80%] md:w-[70%] lg:w-[60%] mx-auto px-4">
              <p class="text-base sm:text-lg font-medium text-center leading-relaxed">
                {{ slide.description }}
              </p>
            </div>
          </div>
        </div>
        <div class="flex items-center justify-center space-x-3">
          <button v-for="(_, index) in slides" :key="index" @click="goToSlide(index)" :class="[
            'w-3 h-3 rounded-full transition-all duration-300',
            currentIndex === index
              ? 'bg-white'
              : 'bg-transparent border-2 opacity-30 hover:bg-white hover:opacity-100',
          ]" />
        </div>
      </div>
      <!-- next arrow -->
      <button @click="nextSlide"
        class="p-3 rounded-full bg-transparent transition-all duration-300 transform hover:scale-125 z-10 flex-shrink-0">
        <MdNavigateNext class="w-9 h-9" />
      </button>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from "vue";
import { MdNavigateNext } from "@kalimahapps/vue-icons";

const slides = [
  {
    littleTitle: "Startup 1",
    mainTitle: "Forget About Code",
    description:
      "Startup Framework gives you complete freedom over your creative process — you don’t have to think about any technical aspects. There are no limits and absolutely no coding.",
  },
  {
    littleTitle: "Startup 2",
    mainTitle: "Launch Faster",
    description:
      "Lorem Ipsum has been the industrys standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, remaining unchanged.",
  },
  {
    littleTitle: "Startup 3",
    mainTitle: "Build Your Dream",
    description:
      "There are many variations of passages of Lorem Ipsum available, but the majority have suffered alteration in some form, by injected humour, or randomised words which dont look even slightly believable.",
  },
  {
    littleTitle: "AI-Powered SaaS",
    mainTitle: "Smarter Decisions",
    description:
      "Leverage real-time insights with our AI-driven dashboards. Our platform analyzes your data continuously to surface trends, predict outcomes, and help your team make faster, more informed decisions.",
  },
  {
    littleTitle: "AI for Startups",
    mainTitle: "Automate Everything",
    description:
      "Free up your team to focus on what matters. Our smart automation tools handle repetitive tasks, improve customer engagement, and streamline operations — no complex setup required.",
  }
];

let intervalId;

const currentIndex = ref(0);

const nextSlide = () => {
  currentIndex.value = (currentIndex.value + 1) % slides.length;
};

const prevSlide = () => {
  currentIndex.value = (currentIndex.value - 1 + slides.length) % slides.length;
};

const goToSlide = (index) => {
  currentIndex.value = index;
};

onMounted(() => {
  intervalId = setInterval(nextSlide, 5000);
});

onBeforeUnmount(() => {
  clearInterval(intervalId);
});
</script>