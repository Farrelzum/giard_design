<script setup>
import { ref } from 'vue'

const isSearchOpen = ref(false)
const toggleSearch = () => isSearchOpen.value = !isSearchOpen.value
</script>

<template>
  <div class="relative flex items-center h-[24px] md:ml-4">
    <button 
      @click="toggleSearch" 
      class="hover:bg-gray-100 text-black transition-colors flex items-center justify-center w-10 h-10 rounded-md focus-visible:ring-2 focus-visible:ring-primary outline-none"
      aria-label="Wyszukaj na stronie"
      :aria-expanded="isSearchOpen"
    >
      <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z" />
      </svg>
    </button>

    <Transition name="fade-slide">
      <div 
        v-show="isSearchOpen" 
        class="absolute top-full right-0 mt-2 w-64 bg-white border border-gray-100 shadow-lg rounded-md p-2 z-20 cursor-default"
      >
        <div class="flex items-center gap-2">
          <input 
            type="text" 
            placeholder="Czego szukasz?"
            class="w-full px-3 py-2 border border-gray-300 rounded-md focus:border-primary focus:ring-1 focus:ring-primary outline-none text-sm text-black"
          >
          <button class="bg-primary hover:bg-green-700 text-white px-3 py-2 rounded-md text-sm transition-colors">
            Szukaj
          </button>
        </div>
      </div>
    </Transition>
  </div>
</template>