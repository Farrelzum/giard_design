<script setup>
import { ref } from 'vue'

defineProps({
  isOpen: {
    type: Boolean,
    required: true
  }
})

const emit = defineEmits(['close'])
const isOfferOpen = ref(false)
const toggleOffer = () => isOfferOpen.value = !isOfferOpen.value
</script>

<template>
  <Transition name="fade-slide">
    <div v-show="isOpen" class="md:hidden bg-white border-t border-gray-100 px-4 py-4 flex flex-col gap-4 shadow-lg absolute w-full left-0 z-40">
      <a href="#" @click="emit('close')" class="text-black font-medium">O nas</a>
      <a href="#" @click="emit('close')" class="text-black font-medium">Realizacje</a>
      
      <div>
        <button @click="toggleOffer" class="flex items-center justify-between w-full text-black font-medium">
          Oferta
          <svg :class="{'rotate-180': isOfferOpen}" class="w-4 h-4 transition-transform duration-200" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7"></path></svg>
        </button>
        <Transition name="fade-slide">
          <div v-show="isOfferOpen" class="flex flex-col gap-2 mt-2 pl-4 border-l-2 border-green-100">
            <a href="#" @click="emit('close')" class="text-black text-sm">Projektowanie</a>
            <a href="#" @click="emit('close')" class="text-black text-sm">Pielęgnacja</a>
            <a href="#" @click="emit('close')" class="text-black text-sm">Nawadnianie</a>
          </div>
        </Transition>
      </div>
      
      <a href="#" @click="emit('close')" class="text-black font-medium">Kontakt</a>

      <div class="flex items-center w-full mt-2">
        <input type="text" placeholder="Szukaj..." class="w-full px-3 py-2 border border-gray-300 rounded-l-md focus:border-primary outline-none text-sm text-black">
        <button class="bg-primary hover:bg-green-700 text-white px-4 py-2 rounded-r-md text-sm transition-colors">Szukaj</button>
      </div>
    </div>
  </Transition>
</template>