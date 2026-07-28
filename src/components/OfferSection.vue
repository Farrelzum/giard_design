<script setup>
import { offers } from '../data/offers.js'
import OfferCard from './OfferCard.vue'
</script>

<template>
  <section class="w-full bg-[#F6F1E9] pt-30 pb-40 md:py-[6rem]">
    <div class="max-w-7xl mx-auto px-4">
      
      <div class="mb-10 md:mb-24 md:mx-25 max-w-2xl">
        <span class="text-sm md:text-[0.875rem] text-primary block mb-2">Oferta</span>
        <h2 class="text-3xl md:text-[3rem] md:leading-[3.5rem] text-black mb-4">
          Działamy <span class="italic">kompleksowo</span>
        </h2>
        <p class="text-gray-700 md:text-[1rem] md:leading-[1.5rem]">
          Oferujemy kompletną obsługę inwestycji terenów zielonych. Projektujemy nowoczesne ogrody przydomowe oraz rezydencjonalne. Stworzymy dla Ciebie projekt, zwizualizujemy go i wcielimy w życie, a na każdym etapie posłużymy radą i wieloletnim doświadczeniem.
        </p>
      </div>
      
      <div class="grid grid-cols-1 lg:grid-cols-3 gap-16 md:gap-[2rem]">
        <OfferCard 
          v-for="(offer, index) in offers" 
          :key="index"
          :offer="offer"
        />
      </div>
      
    </div>
  </section>
</template>