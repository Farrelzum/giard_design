<script setup>
defineProps({
  projects: {
    type: Array,
    required: true
  },
  activeIndex: {
    type: Number,
    default: null
  }
})

defineEmits(['close', 'next', 'prev'])
</script>

<template>
  <Teleport to="body">
    <Transition name="fade">
      <div 
        v-if="activeIndex !== null"
        class="fixed inset-0 z-50 flex items-center justify-center bg-black/95"
        @click.self="$emit('close')"
      >
        <button 
          @click="$emit('close')" 
          class="absolute top-6 right-6 text-white/70 hover:text-white p-2 outline-none"
        >
          <svg xmlns="http://www.w3.org/2000/svg" class="h-8 w-8 md:h-[2rem] md:w-[2rem]" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
          </svg>
        </button>

        <button 
          @click="$emit('prev')" 
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
          @click="$emit('next')" 
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