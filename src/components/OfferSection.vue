<script setup>
    import { offers } from '../data/offers.js'
</script>

<template>
  <section class="w-full bg-[#F6F1E9] pt-30 pb-40 md:py-[6rem]">
    <div class="max-w-7xl mx-auto px-4">
      <div class="mb-10 md:mb-24 mx-25 max-w-2xl">
        <span class="text-sm md:text-[0.875rem] text-primary block mb-2">Oferta</span>
        <h2 class="text-3xl md:text-[3rem] md:leading-[3.5rem] text-black mb-4">
          Działamy <span class="italic font-serif">kompleksowo</span>
        </h2>
        <p class="text-gray-700 md:text-[1rem] md:leading-[1.5rem]">
          Oferujemy kompletną obsługę inwestycji terenów zielonych. Projektujemy nowoczesne ogrody przydomowe oraz rezydencjonalne. Stworzymy dla Ciebie projekt, zwizualizujemy go i wcielimy w życie, a na każdym etapie posłużymy radą i wieloletnim doświadczeniem.
        </p>
      </div>
      <div class="grid grid-cols-1 md:grid-cols-3 gap-16 md:gap-[2rem]">
        <a 
        v-for="(offer, index) in offers" 
        :key="index"
        href="#"
        class="group block bg-white rounded-3xl p-8 md:p-12 transition-all duration-300 hover:-translate-y-2 hover:shadow-xl focus-visible:ring-2 focus-visible:ring-primary outline-none md:max-w-[40rem] md:w-full md:mx-auto lg:max-w-none"
        >
          <div class="w-12 h-12 md:w-[3.5rem] md:h-[3.5rem] flex items-center justify-center rounded-xl mb-6 md:mb-[2rem] transition-transform duration-300 group-hover:scale-110">
            <img :src="offer.icon" :alt="offer.title" class="h-8 w-8 md:h-[2.5rem] md:w-[2.5rem] object-contain" />
          </div>
          
          <h3 class="text-2xl md:text-[1.75rem] text-black mb-8 md:mb-3">
            {{ offer.title }}
          </h3>
          
          <p class="text-gray-700 text-sm md:text-[1rem] md:leading-[1.5rem] mb-10 md:mb-[4rem]">
            {{ offer.description }}
          </p>
          <div class="inline-flex items-center text-primary font-medium border-b border-primary pb-1 group-hover:border-green-700 transition-colors">
            <span class="mr-2">{{ offer.linkText }}</span>
            <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4 md:h-[1.125rem] md:w-[1.125rem] transition-transform duration-300 group-hover:translate-x-1" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M14 5l7 7m0 0l-7 7m7-7H3" />
            </svg>
          </div>
        </a>

      </div>
    </div>
  </section>
</template>