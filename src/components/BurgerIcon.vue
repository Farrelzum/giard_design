<script setup>
defineProps({
  isOpen: {
    type: Boolean,
    required: true
  }
})
const emit = defineEmits(['toggle'])
</script>

<template>
  <button 
    @click="emit('toggle')" 
    class="md:hidden relative w-10 h-10 flex items-center justify-center text-black focus-visible:ring-2 focus-visible:ring-primary outline-none rounded"
    :aria-expanded="isOpen"
    aria-label="Przełącz menu główne"
  >
    <svg 
      xmlns="http://www.w3.org/2000/svg" 
      class="absolute h-6 w-6 transition-all duration-300 ease-in-out" 
      :class="isOpen ? 'opacity-0 rotate-90 scale-50' : 'opacity-100 rotate-0 scale-100'"
      fill="none" viewBox="0 0 24 24" stroke="currentColor"
    >
      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
    </svg>
    
    <svg 
      xmlns="http://www.w3.org/2000/svg" 
      class="absolute h-6 w-6 transition-all duration-300 ease-in-out" 
      :class="isOpen ? 'opacity-100 rotate-0 scale-100' : 'opacity-0 -rotate-90 scale-50'"
      fill="none" viewBox="0 0 24 24" stroke="currentColor"
    >
      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
    </svg>
  </button>
</template>