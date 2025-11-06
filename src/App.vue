<script setup>
import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
<div class="absolute bg-gradient-to-tl from-[#181818] to-[#7E7E7E] min-h-screen flex items-center justify-center w-full h-full">

<div class="absolute top-0 left-0 w-full overflow-hidden leading-[0] h-full">
  <svg
    xmlns="http://www.w3.org/2000/svg"
    viewBox="0 0 1200 120"
    preserveAspectRatio="none"
    class="relative block w-[calc(193%+1.3px)] h-[1000px]"
  >
    <!-- Define the gradient -->
    <defs>
      <linearGradient id="emeraldGradient" x1="0%" y1="0%" x2="100%" y2="100%">
        <stop offset="0%" stop-color="#5A5A5A" /> 
        <stop offset="100%" stop-color="#20FC8F " /> 
      </linearGradient>
    </defs>

    <!-- Use the gradient -->
    <path
      d="M321.39,56.44c58-10.79,114.16-30.13,172-41.86,82.39-16.72,168.19-17.73,250.45-.39C823.78,31,906.67,72,985.66,92.83c70.05,18.48,146.53,26.09,214.34,3V0H0V27.35A600.21,600.21,0,0,0,321.39,56.44Z"
      fill="url(#emeraldGradient)"
    ></path>
  </svg>
</div>

</div>

</template>