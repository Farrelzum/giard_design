<script setup>
defineProps({
  image: {
    type: String,
    required: true
  },
  index: {
    type: Number,
    required: true
  }
})

defineEmits(['open-lightbox'])
</script>

<template>
  <div 
    class="cursor-pointer group"
    @click="$emit('open-lightbox', index)"
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
</template>