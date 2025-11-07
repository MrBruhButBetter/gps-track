
<script setup>
import { ref, onMounted } from 'vue'
import L from 'leaflet'
import 'leaflet/dist/leaflet.css'

// Popup visibility
const showPopup = ref(false)
const email = ref('')

// Leaflet map
onMounted(() => {
  const map = L.map('map').setView([58.25399, 22.48561], 13)

  L.tileLayer('https://tile.openstreetmap.org/{z}/{x}/{y}.png', {
    attribution: '&copy; OpenStreetMap contributors'
  }).addTo(map)

  L.marker([58.25399, 22.48561]).addTo(map)
    .bindPopup('Test :)')
})

// Toggle popup
const togglePopup = () => {
  showPopup.value = !showPopup.value
}

// Simple submit (demo only)
function submitEmail() {
  if (email.value.trim()) {
    alert(`Thanks for joining! (Demo only - email not saved: ${email.value})`)
    email.value = ''
    showPopup.value = false
  }
}
</script>

<template>
<div class="relative flex flex-col min-h-screen w-full bg-gradient-to-tl from-[#181818] to-[#7E7E7E]">

  <!-- Navbar -->
  <nav class="fixed top-0 left-0 w-full flex items-center justify-between p-4 sm:p-6 z-50">
    <a class="w-12 h-12 sm:w-16 sm:h-16" href="#">
      <img src="./assets/Gps/logo.png" alt="logo" class="w-full h-full object-contain">
    </a>
    <ul class="flex gap-6 text-white">
      <a href="#" class="text-sm sm:text-base font-bold">Info →</a>
    </ul>
  </nav>

  <!-- Main content area -->
  <div class="flex-1 relative flex flex-col lg:flex-row items-start justify-center px-4 sm:px-6 md:px-12 lg:px-24 pt-24 sm:pt-32 pb-8 z-0 gap-8">

    <!-- SVG Background -->
    <div class="absolute top-0 left-0 w-full overflow-hidden leading-[0] h-full -z-10">
      <svg
        xmlns="http://www.w3.org/2000/svg"
        viewBox="0 0 1200 120"
        preserveAspectRatio="none"
        class="relative block w-[calc(193%+1.3px)] h-[600px] sm:h-[1000px]"
      >
        <defs>
          <linearGradient id="emeraldGradient" x1="0%" y1="0%" x2="100%" y2="100%">
            <stop offset="0%" stop-color="#5A5A5A" /> 
            <stop offset="100%" stop-color="#20FC8F" /> 
          </linearGradient>
        </defs>
        <path
          d="M321.39,56.44c58-10.79,114.16-30.13,172-41.86,82.39-16.72,168.19-17.73,250.45-.39C823.78,31,906.67,72,985.66,92.83c70.05,18.48,146.53,26.09,214.34,3V0H0V27.35A600.21,600.21,0,0,0,321.39,56.44Z"
          fill="url(#emeraldGradient)"
        ></path>
      </svg>
    </div>

    <!-- Left content section -->
    <div class="flex-1 flex flex-col items-start justify-center w-full lg:w-auto">
      <h1 class="text-white text-2xl sm:text-3xl md:text-4xl font-bold mb-4 sm:mb-6 max-w-xl text-left">
        Track Every Construction Vehicle. Anytime. Anywhere.
      </h1>

      <p class="text-white/80 text-sm sm:text-base md:text-lg mb-6 sm:mb-10 max-w-xl text-left">
        A smart tracking platform built for construction companies to
        monitor vehicles in real time, prevent theft, and keep customers
        informed.
      </p>

      <h1 class="flex items-center gap-1 sm:gap-2 text-white text-3xl sm:text-4xl md:text-6xl font-bold mb-6 sm:mb-10 justify-start flex-wrap">
        Comming S
        <img class="w-12 h-12 sm:w-16 sm:h-16 md:w-20 md:h-20 inline-block" src="../src/../src/assets/Gps/AirTag1.png" alt="">
        <img class="w-12 h-12 sm:w-16 sm:h-16 md:w-20 md:h-20 inline-block" src="../src/assets/Gps/AirTag2.png" alt="">
        n
      </h1>

      <div class="flex flex-col sm:flex-row items-start sm:items-center gap-4 sm:gap-6 mb-6 sm:mb-10 w-full lg:w-auto">
        <button 
          @click="togglePopup"
          class="bg-[#D9D9D9] px-6 py-3 sm:p-5 rounded-3xl shadow-xl text-black font-bold hover:scale-105 transition-transform w-full sm:w-auto text-center"
        >
          Join our wait-list
        </button>
        <p class="text-white/80 text-xs sm:text-sm md:text-base max-w-xl text-left leading-relaxed">
          Be the first to try it when we launch!<br>
          No spam — just one early access<br>
          invite when we go live.
        </p>
      </div>
    </div>

    <!-- Map section -->
    <div class="w-full lg:w-[40%] h-64 sm:h-80 lg:h-96 rounded-3xl shadow-lg overflow-hidden">
      <div id="map" class="w-full h-full"></div>
    </div>

  </div>

  <!-- Footer -->
  <footer class="bg-black w-full py-4 sm:py-6 text-center text-white text-xs sm:text-sm mt-auto">
    <p>© 2025 Construction Vehicle Tracker — All rights reserved.</p>
    <p>Built with ❤️ by our development team.</p>
  </footer>

  <!-- Popup Modal -->
  <div 
    v-if="showPopup"
    class="fixed inset-0 bg-black/70 flex items-center justify-center z-50 p-4"
  >
    <div class="relative bg-white text-black p-6 sm:p-8 rounded-3xl shadow-2xl max-w-md w-full overflow-hidden">
      
      <!-- White wavy SVG background -->
      <div class="absolute top-0 left-0 w-full overflow-hidden leading-[0] h-full -z-10 opacity-70">
        <svg
          xmlns="http://www.w3.org/2000/svg"
          viewBox="0 0 1200 120"
          preserveAspectRatio="none"
          class="relative block w-[calc(150%+1.3px)] h-[400px]"
        >
          <defs>
            <linearGradient id="whiteWave" x1="0%" y1="0%" x2="100%" y2="100%">
              <stop offset="0%" stop-color="#ffffff" />
              <stop offset="100%" stop-color="#f2f2f2" />
            </linearGradient>
          </defs>
          <path
            d="M321.39,56.44c58-10.79,114.16-30.13,172-41.86,82.39-16.72,168.19-17.73,250.45-.39C823.78,31,906.67,72,985.66,92.83
               c70.05,18.48,146.53,26.09,214.34,3V0H0V27.35
               A600.21,600.21,0,0,0,321.39,56.44Z"
            fill="url(#whiteWave)"
          ></path>
        </svg>
      </div>

      <!-- Popup content -->
      <h2 class="text-xl sm:text-2xl font-bold mb-4 relative z-10">Join Our Waitlist 🚀</h2>
      <p class="mb-6 text-gray-700 relative z-10 text-sm sm:text-base">
        Thank you for your interest! We're launching soon.  
        Enter your email below to be the first to get access.
      </p>
      <input 
        v-model="email"
        type="email" 
        placeholder="Mail.Sean@example.com" 
        class="rounded-xl p-3 w-full mb-4 border border-gray-300 focus:outline-none focus:ring-2 focus:ring-emerald-400 relative z-10"
      />
      <div class="flex flex-col sm:flex-row justify-center gap-3 sm:gap-4 relative z-10">
        <button 
          @click="togglePopup" 
          class="bg-gray-800 text-white px-6 py-2 rounded-xl hover:bg-gray-700 transition w-full sm:w-auto"
        >
          Close
        </button>
        <button 
          @click="submitEmail"
          class="bg-emerald-500 hover:bg-emerald-600 text-white px-6 py-2 rounded-xl transition w-full sm:w-auto"
        >
          Submit
        </button>
      </div>
    </div>
  </div>

</div>
</template>


