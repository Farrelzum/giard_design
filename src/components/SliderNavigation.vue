<script setup>
defineEmits(['prev', 'next'])
</script>

<template>
  <div class="flex absolute top-[14.75rem] md:top-auto md:bottom-0 right-0 bg-[#F6F1E9] shadow-sm z-10">
    <button 
      @click="$emit('prev')" 
      class="w-[4rem] h-[4rem] flex items-center justify-center hover:bg-gray-100 transition-colors focus-visible:ring-2 focus-visible:ring-inset focus-visible:ring-primary outline-none"
      aria-label="Poprzedni slajd"
    >
      <svg xmlns="http://www.w3.org/2000/svg" class="h-[1.5rem] w-[1.5rem] text-black" fill="none" viewBox="0 0 24 24" stroke="currentColor">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 19l-7-7m0 0l7-7m-7 7h18" />
      </svg>
    </button>
    
    <button 
      @click="$emit('next')" 
      class="w-[4rem] h-[4rem] flex items-center justify-center hover:bg-gray-100 transition-colors focus-visible:ring-2 focus-visible:ring-inset focus-visible:ring-primary outline-none"
      aria-label="Następny slajd"
    >
      <svg xmlns="http://www.w3.org/2000/svg" class="h-[1.5rem] w-[1.5rem] text-black" fill="none" viewBox="0 0 24 24" stroke="currentColor">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M14 5l7 7m0 0l-7 7m7-7H3" />
      </svg>
    </button>
  </div>
</template>