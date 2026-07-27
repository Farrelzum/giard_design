<script setup>
import { ref } from 'vue'

const isOfferOpen = ref(false)
const toggleOffer = () => isOfferOpen.value = !isOfferOpen.value
</script>

<template>
  <div class="flex items-center md:gap-12">
    
    <div class="relative">
      <button 
        @click="toggleOffer" 
        class="flex items-center gap-1 text-black text-sm hover:text-green-600 transition-colors md:text-base focus-visible:ring-2 outline-none rounded"
        :aria-expanded="isOfferOpen"
      >
        Oferta
        <svg :class="{'rotate-180': isOfferOpen}" class="w-4 h-4 transition-transform duration-200" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7"></path></svg>
      </button>
      
      <Transition name="fade-slide">
        <ul v-show="isOfferOpen" class="absolute left-0 mt-2 w-48 bg-white border border-gray-100 shadow-lg rounded-md py-2 flex flex-col z-20">
          <li><a href="#" class="text-black text-sm block px-4 py-2 hover:bg-green-50 hover:text-green-700 transition-colors">Projektowanie</a></li>
          <li><a href="#" class="text-black text-sm block px-4 py-2 hover:bg-green-50 hover:text-green-700 transition-colors">Pielęgnacja</a></li>
          <li><a href="#" class="text-black text-sm block px-4 py-2 hover:bg-green-50 hover:text-green-700 transition-colors">Nawadnianie</a></li>
        </ul>
      </Transition>
    </div>

    <a href="#" class="text-black text-sm hover:text-green-600 transition-colors md:text-base focus-visible:ring-2 outline-none rounded">O firmie</a>
    <a href="#" class="text-black text-sm hover:text-green-600 transition-colors md:text-base focus-visible:ring-2 outline-none rounded">Realizacje</a>
    <a href="#" class="text-black text-sm hover:text-green-600 transition-colors md:text-base focus-visible:ring-2 outline-none rounded">Kontakt</a>
    
  </div>
</template>