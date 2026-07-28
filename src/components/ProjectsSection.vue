<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import Macy from 'macy'
import { projectsPhotos } from '../data/projects.js'
import ProjectCard from './ProjectCard.vue'
import ProjectLightbox from './ProjectLightbox.vue'

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
        <ProjectCard 
          v-for="(image, index) in projects" 
          :key="index"
          :image="image"
          :index="index"
          @open-lightbox="openLightbox"
        />
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

  <ProjectLightbox 
      :projects="projects" 
      :active-index="activeIndex" 
      @close="closeLightbox" 
      @next="nextPhoto" 
      @prev="prevPhoto" 
  />
</template>