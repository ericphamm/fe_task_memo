<template>
    <section class="relative">
    <nav 
      :class="[
        'fixed left-0 right-0 z-50 transition-all duration-200',
        isScrolled || isMenuOpen
          ? 'bg-white shadow-md top-0' 
          : 'bg-transparent top-0 md:top-5'
      ]"
    >
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="flex items-center justify-between h-16">
          <!-- desktop nav -->
          <div class="hidden md:flex justify-center w-full">
            <ul class="flex items-center space-x-8">
            <li><a href="#home" :class="navLinkClass()">Home</a></li>
            <li><a href="#features" :class="navLinkClass()">Features</a></li>
            <li><a href="#pricing" :class="navLinkClass()">Pricing</a></li>
            <li><a href="#cta" :class="navLinkClass()">Blog</a></li>
            <li><a href="#contact" :class="navLinkClass()">Contact</a></li>
            <li><a href="#pricing" :class="navLinkClass()">
                <AkDribbbleFill :class="navLinkClass()" />
            </a></li>
            <li><a href="#contact" :class="navLinkClass()">
              <AkBehanceFill class="w-5 h-5" />
            </a></li>
            </ul>
           </div>

          <!-- humburger button -->
         
          <div class="md:hidden ml-auto">
            <button
              @click="toggleMenu"
              :class="['p-2 rounded-md transition-colors duration-300',
              isMenuOpen
              ? 'bg-white text-indigo-700'
              : isScrolled
                ? 'text-indigo-700'
                : 'text-white'
              ]"
              :aria-expanded="isMenuOpen"
              aria-label="Toggle nav menu"
            >
            <FaBars 
            v-if="!isMenuOpen" 
            :class="[
  'w-8 h-8 transition-colors duration-300',
  isMenuOpen
    ? 'text-indigo-700'
    : isScrolled
      ? 'text-indigo-700'
      : 'text-white'
]"/>
            <AkXSmall 
            v-if="isMenuOpen" 
            :class="[
            'w-8 h-8 transition-colors duration-300',
            isScrolled.value ? 'text-indigo-700' : 'text-indigo-700']"/>
            </button>
          </div>
        
        </div>

        <!-- mobile nav-->
        <div 
          :class="[
            'md:hidden transition-all duration-300 ease-in-out overflow-hidden',
            isMenuOpen ? 'opacity-100' : 'max-h-0 opacity-0']">
          <div 
            :class="[
              'px-4 pt-2 pb-3 rounded-lg mt-2',
              isScrolled ? 'bg-white shadow-lg' : 'bg-white/70 backdrop-blur-sm'
            ]">
            <ul class="flex flex-col items-center space-y-1 w-[80%] mx-auto">
              <li>
                <a href="#home" @click="closeMenu" :class="navLinkClassMobile()">Home</a>
              </li>
              <li>
                <a href="#features" @click="closeMenu" :class="navLinkClassMobile()">Features</a>
              </li>
              <li>
                <a href="#pricing" @click="closeMenu" :class="navLinkClassMobile()">Pricing</a>
              </li>
              <li>
                <a href="#cta" @click="closeMenu" :class="navLinkClassMobile()">Blog</a>
              </li>
              <li>
                <a href="#contac" @click="closeMenu" :class="navLinkClassMobile()">Contact</a>
              </li>
              <li><a href="#cta" @click="closeMenu" :class="navLinkIconClassMobile()">
                  <AkDribbbleFill class="w-5 h-5" />
                 </a>
                </li>
              <li><a href="#contact" @click="closeMenu" :class="navLinkIconClassMobile()">
                <AkBehanceFill class="w-5 h-5" />
                  </a>
              </li>
            </ul>
          </div>
        </div>

        
      </div>
    </nav>  
    </section>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import { FaBars } from '@kalimahapps/vue-icons'
import { AkXSmall } from '@kalimahapps/vue-icons'
import { AkBehanceFill } from '@kalimahapps/vue-icons'
import { AkDribbbleFill } from '@kalimahapps/vue-icons'

const isMenuOpen = ref(false)
const isScrolled = ref(false)

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value
}

const closeMenu = () => {
  isMenuOpen.value = false
}

const handleScroll = () => {
  isScrolled.value = window.scrollY > 50
}
onMounted(() => {
  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})

function navLinkClass() {
  return [
    'text-[18px] font-medium transition-colors duration-300 hover:opacity-80',
    isScrolled.value ? 'text-indigo-700' : 'text-white hover:opacity-30'
  ]
}

function navLinkClassMobile() {
  return [
    'block px-3 py-2 text-lg text-indigo-700 text-center font-medium transition-colors duration-200 hover:opacity-80 rounded-md hover:bg-blue-100',
    isScrolled.value ? 'text-indigo-700' : 'text-white hover:opacity-30'
  ]
}

function navLinkIconClassMobile() {
  return [
    'block text-center px-4 py-2 rounded text-indigo-700 text-lg font-medium transition-colors duration-200 hover:text-blue-900 hover:bg-blue-100'
  ]
}

</script>
