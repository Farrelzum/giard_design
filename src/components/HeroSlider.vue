<script setup>
import { ref } from 'vue'
import { slides } from '../data/slides.js'
import HeroSlide from './HeroSlide.vue'
import SliderNavigation from './SliderNavigation.vue'

const currentSlide = ref(0)

const nextSlide = () => {
  currentSlide.value = (currentSlide.value + 1) % slides.length
}

const prevSlide = () => {
  currentSlide.value = (currentSlide.value - 1 + slides.length) % slides.length
}

const touchStartX = ref(0)
const touchEndX = ref(0)

const handleTouchStart = (e) => {
  touchStartX.value = e.changedTouches[0].screenX
}

const handleTouchEnd = (e) => {
  touchEndX.value = e.changedTouches[0].screenX
  handleSwipe()
}

const handleSwipe = () => {
  const swipeThreshold = 50
  
  if (touchEndX.value < touchStartX.value - swipeThreshold) {
    nextSlide()
  }
  if (touchEndX.value > touchStartX.value + swipeThreshold) {
    prevSlide()
  }
}
</script>

<template>
  <section 
    class="relative w-full overflow-hidden bg-secondary"
    @touchstart="handleTouchStart"
    @touchend="handleTouchEnd"
  >
    <div 
      class="flex transition-transform duration-700 ease-in-out"
      :style="{ transform: `translateX(-${currentSlide * 100}%)` }"
    >
      <HeroSlide 
        v-for="(slide, index) in slides" 
        :key="index" 
        :slide="slide" 
      />
    </div>

    <SliderNavigation @prev="prevSlide" @next="nextSlide" />
    
  </section>
</template>