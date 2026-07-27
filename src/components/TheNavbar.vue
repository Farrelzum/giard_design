<script setup>
import { ref } from 'vue'
import MobileMenu from './MobileMenu.vue'
import BurgerIcon from './BurgerIcon.vue'
import TabletNavLinks from './TabletNavLinks.vue'
import SearchBar from './SearchBar.vue'

const isMobileMenuOpen = ref(false)
const toggleMobileMenu = () => isMobileMenuOpen.value = !isMobileMenuOpen.value
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
        <SearchBar />
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