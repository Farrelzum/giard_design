<script setup>
import { ref } from 'vue'
import MobileMenu from './MobileMenu.vue'
import BurgerIcon from './BurgerIcon.vue'
import TabletNavLinks from './TabletNavLinks.vue'

const isMobileMenuOpen = ref(false)
const isSearchOpen = ref(false)

const toggleMobileMenu = () => isMobileMenuOpen.value = !isMobileMenuOpen.value
const toggleSearch = () => isSearchOpen.value = !isSearchOpen.value
</script>

<template>
  <header class="relative w-full bg-white shadow-sm z-50">
    <nav class="flex items-center justify-between px-4 py-4 md:py-6 max-w-7xl mx-auto">
      
      <a href="/" class="focus-visible:ring-2 focus-visible:ring-green-600 outline-none rounded" aria-label="Strona główna">
        <img src="../assets/logo.svg" alt="Logo firmy ogrodniczej" class="w-[115px] h-[19px] md:w-[7.1875rem] md:h-[1.1875rem]" />
      </a>

      <BurgerIcon 
        :isOpen="isMobileMenuOpen" 
        @toggle="toggleMobileMenu" 
      />

     <div class="hidden md:flex items-center">
        <TabletNavLinks />
        <div class="relative flex items-center md:ml-4">
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
      </div>
    </nav>
    <MobileMenu 
      :isOpen="isMobileMenuOpen" 
      @close="isMobileMenuOpen = false" 
    />
  </header>
</template>

<style>
.fade-slide-enter-active,
.fade-slide-leave-active {
  transition: opacity 0.3s ease, transform 0.3s ease;
}
.fade-slide-enter-from,
.fade-slide-leave-to {
  opacity: 0;
  transform: translateY(-10px);
}
</style>