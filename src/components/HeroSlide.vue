<script setup>
defineProps({
  slide: {
    type: Object,
    required: true
  }
})
</script>

<template>
  <div class="w-full flex-shrink-0 relative flex flex-col md:block">
    <div class="w-full h-[18.75rem] md:h-full md:absolute md:top-0 md:right-0 md:w-1/2">
      <img :src="slide.image" :alt="slide.title" class="w-full h-full object-cover" draggable="false" />
    </div>
    <div class="relative max-w-7xl mx-auto px-4 w-full md:min-h-[45rem] flex items-center">
      
      <div class="w-full md:w-1/2 md:pr-12 pt-10 pb-16 md:py-[6rem]">
        
        <h1 class="text-4xl md:text-[3.5rem] md:leading-[4rem] text-black font-semibold mb-[2.75rem] whitespace-pre-line tracking-tight">
          {{ slide.title }}
        </h1>
        
        <p class="text-base md:text-[1rem] md:leading-[1.75rem] text-gray-800 mb-[4.5rem] max-w-md">
          {{ slide.description }}
        </p>
        
        <div class="flex flex-col lg:flex-row items-start lg:items-center gap-[1rem] md:gap-[2.25rem]">
          <button class="bg-primary hover:bg-green-700 text-white px-8 md:px-[2rem] py-3 md:py-[0.875rem] rounded-full text-sm font-medium transition-colors focus-visible:ring-2 focus-visible:ring-primary outline-none">
            Skontaktuj się z nami
          </button>
          
          <button class="border border-primary text-primary hover:bg-black/5 px-8 md:px-[2rem] py-3 md:py-[0.875rem] rounded-full text-sm font-medium transition-colors flex items-center gap-2 focus-visible:ring-2 focus-visible:ring-primary outline-none">
            Zobacz nasze realizacje
            <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4 md:h-[1.125rem] md:w-[1.125rem]" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 14l-7 7m0 0l-7-7m7 7V3" />
            </svg>
          </button>
        </div>

      </div>
    </div>
  </div>
</template>