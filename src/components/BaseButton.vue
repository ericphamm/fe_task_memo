<template>
	<a
	  :href="href"
	  class="inline-flex items-center justify-center text-white rounded-full text-[18px] font-medium transition-all duration-300 transform hover:scale-105"
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





