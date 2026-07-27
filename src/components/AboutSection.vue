<script setup>
import aboutImage from '../assets/images/about_image.png'
</script>

<template>
  <section class="relative w-full bg-[#1B5B31]">
    <div class="w-full h-[20rem] md:h-full md:absolute md:top-0 md:left-0 md:w-[45%]">
      <img :src="aboutImage" alt="O firmie" class="w-full h-full object-cover" />
    </div>
    <div class="relative max-w-7xl mx-auto px-4 flex justify-end">
      <div class="w-full md:w-1/2 py-16 md:py-[6rem] md:pl-[3rem] lg:pl-[4rem]">
        
        <span class="text-sm md:text-[0.875rem] text-about block mb-4">O firmie</span>
        
        <h2 class="text-3xl md:text-[3rem] md:leading-[3.5rem] text-about mb-6 md:mb-10">
          Tworzymy <br class="hidden md:block" />
          <span class="italic">z pasją</span>
        </h2>
        
        <p class="text-about text-sm md:text-[1rem] md:leading-[1.5rem] mb-10 md:mb-[4.5rem]">
          Każdy projekt to nowe wyzwanie. Dlatego nasz zespół tworzą wykwalifikowani projektanci oraz architekci, których zadaniem jest rozpoznanie i realizacja potrzeb każdego Klienta. Nasza specjalizacja to przestrzenie nowoczesne, które charakteryzuje minimalizm, geometria i elegancka prostota. Tworzymy ogrody małoobsługowe, dostosowane do współczesnego trybu życia.
        </p>
        
        <button class="border border-about text-about hover:bg-white hover:text-[#1B5B31] px-8 md:px-[2rem] py-3 md:py-[0.875rem] rounded-full text-sm font-medium transition-colors flex items-center gap-2 focus-visible:ring-2 focus-visible:ring-white outline-none w-fit">
          Poznaj nas bliżej
          <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4 md:h-[1.125rem] md:w-[1.125rem]" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M14 5l7 7m0 0l-7 7m7-7H3" />
          </svg>
        </button>
        
      </div>
    </div>
    
  </section>
</template>