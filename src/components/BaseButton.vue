<template>
	<a
	  :href="href"
	  class="inline-flex items-center justify-center text-white px-14 h-[70px] rounded-full text-[18px] font-medium transition-all duration-300 transform hover:scale-105"
	>
	  {{ text }}
	</a>
  </template>
  
  <script setup>
  defineProps({
	href: String,
	text: String,
  });
  </script>


<!-- bg-[#25DAC5] hover:bg-[#00e69a] -->



