<template>
  <div
    class="relative w-full m-h-[600px] flex items-center justify-center px-4 text-white overflow-hidden"
  >
    <div class="flex flex-col mx-auto items-center space-y-14 py-4">
      <div
        class="flex transition-transform duration-700 ease-in-out w-full max-w-6xl"
        :style="{ transform: `translateX(-${currentIndex * 100}%)` }"
      >
        <div
          v-for="(slide, index) in slides"
          :key="index"
          class="w-full flex-shrink-0 text-center space-y-6"
        >
          <p class="text-2xl font-bold">{{ slide.littleTitle }}</p>
          <h1
            class="text-3xl sm:text-4xl md:text-5xl lg:text-6xl font-bold leading-tight break-words px-2"
          >
            {{ slide.mainTitle }}
          </h1>
          <div class="w-[60%] mx-auto">
            <p class="text-base sm:text-lg font-medium text-center leading-relaxed">
              {{ slide.description }}
            </p>
          </div>
        </div>
      </div>

      <div class="flex items-center justify-center space-x-3">
        <button
          v-for="(_, index) in slides"
          :key="index"
          @click="goToSlide(index)"
          :class="[
            'w-3 h-3 rounded-full transition-all duration-300',
            currentIndex === index
              ? 'bg-white'
              : 'bg-transparent border-2 opacity-30 hover:bg-white hover:opacity-100',
          ]"
        />
      </div>
    <BaseButton href="" class="bg-[#482BE7] hover:bg-blue-700 h-[60px] px-9 text-[18px]" text="Create an Account" />

    </div>

    <button
      @click="prevSlide"
      class="absolute left-4 md:left-8 top-1/2 -translate-y-1/2 z-10 p-3 rounded-full bg-transparent transition-all duration-300 transform hover:scale-125"
    >
      <MdNavigateNext class="w-9 h-9 rotate-180" />
    </button>

    <button
      @click="nextSlide"
      class="absolute right-4 md:right-8 top-1/2 -translate-y-1/2 p-3 z-10 rounded-full bg-transparent transition-all duration-300 transform hover:scale-125"
    >
      <MdNavigateNext class="w-9 h-9" />
    </button>
  </div>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue'
import { MdNavigateNext } from '@kalimahapps/vue-icons'
import BaseButton from './BaseButton.vue';

const slides = [
  {
    littleTitle: 'Startup 1',
    mainTitle: 'Forget About Code',
    description:
      'Startup Framework gives you complete freedom over your creative process — you don’t have to think about any technical aspects. There are no limits and absolutely no coding.',
  },
  {
    littleTitle: 'Startup 2',
    mainTitle: 'Launch Faster',
    description:
      'Lorem Ipsum has been the industrys standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, remaining unchanged.',
  },
  {
    littleTitle: 'Startup 3',
    mainTitle: 'Build Your Dream',
    description:
      'There are many variations of passages of Lorem Ipsum available, but the majority have suffered alteration in some form, by injected humour, or randomised words which dont look even slightly believable.',
  },
]


let intervalId;

const currentIndex = ref(0)

const nextSlide = () => {
  currentIndex.value = (currentIndex.value + 1) % slides.length
}

const prevSlide = () => {
  currentIndex.value = (currentIndex.value - 1 + slides.length) % slides.length
}

const goToSlide = (index) => {
  currentIndex.value = index
}

onMounted(() => {
  intervalId = setInterval(nextSlide, 5000)
})

onBeforeUnmount(() => {
  clearInterval(intervalId)
})
</script>
