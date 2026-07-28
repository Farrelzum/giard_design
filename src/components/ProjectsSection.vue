<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import Macy from 'macy'
import { projectsPhotos } from '../data/projects.js'

const macyContainer = ref(null)
const projects = ref(projectsPhotos)
let macyInstance = null

const isExpanded = ref(false)
const toggleExpand = () => {
  isExpanded.value = !isExpanded.value
  setTimeout(() => {
    if (macyInstance) macyInstance.recalculate(true)
  }, 1000)
}

const activeIndex = ref(null)

const openLightbox = (index) => {
  activeIndex.value = index
  document.body.style.overflow = 'hidden'
}

const closeLightbox = () => {
  activeIndex.value = null
  document.body.style.overflow = ''
}

const nextPhoto = () => {
  if (activeIndex.value !== null) {
    activeIndex.value = (activeIndex.value + 1) % projects.value.length
  }
}

const prevPhoto = () => {
  if (activeIndex.value !== null) {
    activeIndex.value = (activeIndex.value - 1 + projects.value.length) % projects.value.length
  }
}

const handleKeydown = (e) => {
  if (activeIndex.value === null) return
  if (e.key === 'Escape') closeLightbox()
  if (e.key === 'ArrowRight') nextPhoto()
  if (e.key === 'ArrowLeft') prevPhoto()
}

onMounted(() => {
  macyInstance = Macy({
    container: macyContainer.value,
    trueOrder: false,
    waitForImages: true,
    margin: {
      x: 32,
      y: 32
    },
    columns: 3,
    breakAt: {
      1024: 3,
      768: {
        margin: { x: 32, y: 32 },
        columns: 2
      },
      640: {
        margin: { x: 24, y: 24 },
        columns: 1
      }
    }
  })

  window.addEventListener('keydown', handleKeydown)
})

onUnmounted(() => {
  window.removeEventListener('keydown', handleKeydown)
  if (macyInstance) {
    macyInstance.remove()
  }
})
</script>

<template>
  <section class="w-full bg-secondary py-16 md:py-[6rem] lg:pt-30 lg:pb-11">
    <div class="max-w-7xl lg:mx-auto">
      
      <div class="mb-10 md:mb-[5rem]">
        <span class="text-sm md:text-[0.875rem] text-primary block mb-2">Realizacje</span>
        <h2 class="text-3xl md:text-[3rem] md:leading-[3.5rem] text-black">
          Nasze <span class="italic">projekty</span>
        </h2>
      </div>

      <div 
        class="relative transition-all duration-1000 ease-in-out overflow-hidden"
        :class="isExpanded ? 'max-h-[5000px]' : 'max-h-[50rem] md:max-h-[70rem]'"
      >
        
        <div ref="macyContainer">
          <div 
            v-for="(image, index) in projects" 
            :key="index"
            class="cursor-pointer group"
            @click="openLightbox(index)"
          >
            <div class="relative overflow-hidden">
              <img 
                :src="image" 
                :alt="`Realizacja ${index + 1}`" 
                class="w-full block object-cover transition-transform duration-500 group-hover:scale-105"
              />
              <div class="absolute inset-0 bg-black/0 group-hover:bg-black/20 transition-colors duration-300 flex items-center justify-center">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-10 w-10 text-white opacity-0 group-hover:opacity-100 transition-opacity duration-300 transform scale-50 group-hover:scale-100" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0zM10 7v3m0 0v3m0-3h3m-3 0H7" />
                </svg>
              </div>
            </div>
          </div>
        </div>
        <div 
        v-if="!isExpanded" 
        class="absolute bottom-0 left-0 w-full h-[25rem] bg-gradient-to-t from-about to-about/0 pointer-events-none z-10"
        ></div>
      </div>
      <div class="flex justify-center mt-8 relative z-20">
        <button 
          @click="toggleExpand"
          class="border border-black text-black hover:bg-black hover:text-white px-8 md:px-[2rem] py-3 md:py-[0.875rem] rounded-full text-sm md:text-[1rem] font-medium transition-colors flex items-center gap-2 outline-none focus-visible:ring-2 focus-visible:ring-black"
        >
          {{ isExpanded ? 'Zwiń' : 'Rozwiń' }}
          <svg 
            xmlns="http://www.w3.org/2000/svg" 
            class="h-4 w-4 transition-transform duration-300" 
            :class="isExpanded ? 'rotate-180' : ''"
            fill="none" 
            viewBox="0 0 24 24" 
            stroke="currentColor"
          >
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 14l-7 7m0 0l-7-7m7 7V3" />
          </svg>
        </button>
      </div>

    </div>
  </section>

  <Teleport to="body">
    <Transition name="fade">
      <div 
        v-if="activeIndex !== null"
        class="fixed inset-0 z-50 flex items-center justify-center bg-black/95"
        @click.self="closeLightbox"
      >
        <button 
          @click="closeLightbox" 
          class="absolute top-6 right-6 text-white/70 hover:text-white p-2 outline-none"
        >
          <svg xmlns="http://www.w3.org/2000/svg" class="h-8 w-8 md:h-[2rem] md:w-[2rem]" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
          </svg>
        </button>

        <button 
          @click="prevPhoto" 
          class="absolute left-4 md:left-[2rem] text-white/70 hover:text-white p-4 outline-none hidden md:block"
        >
          <svg xmlns="http://www.w3.org/2000/svg" class="h-10 w-10 md:h-[3rem] md:w-[3rem]" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7" />
          </svg>
        </button>

        <img 
          :src="projects[activeIndex]" 
          class="max-w-[90vw] max-h-[90vh] object-contain select-none"
          alt="Podgląd projektu"
        />

        <button 
          @click="nextPhoto" 
          class="absolute right-4 md:right-[2rem] text-white/70 hover:text-white p-4 outline-none hidden md:block"
        >
          <svg xmlns="http://www.w3.org/2000/svg" class="h-10 w-10 md:h-[3rem] md:w-[3rem]" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
          </svg>
        </button>
      </div>
    </Transition>
  </Teleport>
</template>

<style scoped>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s ease;
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>