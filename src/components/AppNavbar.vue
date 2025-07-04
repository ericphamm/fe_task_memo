<template>
  <nav class="absolute top-0 left-0 w-full flex justify-center z-10 py-12">
    <ul class="hidden md:flex space-x-12 items-center">
      <li>
        <a
          href="#home"
          class="text-white text-lg font-medium text-opacity-30 hover:text-opacity-100"
        >
          Home
        </a>
      </li>
      <li>
        <a
          href="#features"
          class="text-white text-lg font-medium text-opacity-100 hover:text-opacity-50"
        >
          Features
        </a>
      </li>
      <li>
        <a
          href="#pricing"
          class="text-white text-lg font-medium text-opacity-100 hover:text-opacity-50"
          >Pricing
        </a>
      </li>
      <li>
        <a
          href="#blog"
          class="text-white text-lg font-medium text-opacity-100 hover:text-opacity-50"
        >
          Blog
        </a>
      </li>
      <li>
        <a
          href="#globe"
          class="text-white text-lg font-medium text-opacity-100 hover:text-opacity-50"
        >
          <AkDribbbleFill class="w-5 h-5" />
        </a>
      </li>
      <li>
        <a
          href="#be"
          class="text-white text-lg font-medium text-opacity-100 hover:text-opacity-50"
        >
          <AkBehanceFill class="w-6 h-6" />
        </a>
      </li>
    </ul>

    <!-- Humberger menu button -->
    <button
      class="md:hidden text-white absolute top-8 right-8 pr-2 z-20"
      @click="isMenuOpen = !isMenuOpen"
    >
      <FaBars v-if="!isMenuOpen" class="w-8 h-8 text-white" />
      <AkXSmall v-if="isMenuOpen" class="w-8 h-8 text-blue-700" />
    </button>

    <!-- mobile menu -->
    <div v-if="isMenuOpen" class="absolute top-0 left-0 w-full bg-white pt-20 pb-10">
      <ul class="space-y-1 w-[80%] mx-auto">
        <li>
          <a
            href="#home"
            @click="closeMenu"
            class="block text-center px-4 py-2 rounded text-blue-700 text-lg font-medium transition-colors duration-200 hover:text-blue-900 hover:bg-blue-100"
            >Home</a
          >
        </li>
        <li>
          <a
            href="#features"
            @click="closeMenu"
            class="block text-center px-4 py-2 rounded text-blue-700 text-lg font-medium transition-colors duration-200 hover:text-blue-900 hover:bg-blue-100"
            >Features</a
          >
        </li>
        <li>
          <a
            href="#pricing"
            @click="closeMenu"
            class="block text-center px-4 py-2 rounded text-blue-700 text-lg font-medium transition-colors duration-200 hover:text-blue-900 hover:bg-blue-100"
            >Pricing</a
          >
        </li>
        <li>
          <a
            href="#blog"
            @click="closeMenu"
            class="block text-center px-4 py-2 rounded text-blue-700 text-lg font-medium transition-colors duration-200 hover:text-blue-900 hover:bg-blue-100"
            >Blog</a
          >
        </li>
        <li>
          <a
            href="#dribble"
            @click="closeMenu"
            class="block text-center px-4 py-2 rounded text-blue-700 text-lg font-medium transition-colors duration-200 hover:text-blue-900 hover:bg-blue-100"
          >
            <div class="flex justify-center">
              <AkDribbbleFill class="w-6 h-6" />
            </div>
          </a>
        </li>
        <li>
          <a
            href="#be"
            @click="closeMenu"
            class="block text-center px-4 py-2 rounded text-blue-700 text-lg font-medium transition-colors duration-200 hover:text-blue-900 hover:bg-blue-100"
          >
            <div class="flex justify-center">
              <AkBehanceFill class="w-6 h-6" />
            </div>
          </a>
        </li>
      </ul>
    </div>
  </nav>
</template>

<script setup>
import { ref } from 'vue'
import { FaBars } from '@kalimahapps/vue-icons'
import { AkXSmall } from '@kalimahapps/vue-icons'
import { AkBehanceFill } from '@kalimahapps/vue-icons'
import { AkDribbbleFill } from '@kalimahapps/vue-icons'
const isMenuOpen = ref(false)
function closeMenu() {
  isMenuOpen.value = false
}
</script>
