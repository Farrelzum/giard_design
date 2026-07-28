<script setup>
</script>

<template>
  <footer class="w-full bg-[#111111] text-about pt-16 md:pt-[4rem] pb-10 md:pb-[2.5rem]">
    <div class="max-w-7xl mx-auto px-4">
      <div class="flex flex-col md:flex-row justify-between items-start md:items-center mb-10 md:mb-[2.5rem] gap-8 md:gap-0">
      <a href="/" class="focus-visible:ring-2 focus-visible:ring-green-600 outline-none rounded" aria-label="Strona główna">
        <img src="../assets/logo_white.svg" alt="Logo firmy ogrodniczej" class="w-[115px] h-[19px] md:w-[7.1875rem] md:h-[1.1875rem]" />
      </a>
        <div class="flex flex-col md:flex-row items-start md:items-center gap-6 md:gap-[1.5rem] lg:gap-[2rem] w-full md:w-auto">
          <p class="text-sm md:text-[0.875rem] lg:text-[1rem]">Daj znać, co możemy dla Ciebie zrobić!</p>
          <button class="bg-primary hover:bg-primary/90 text-white px-8 md:px-[1.5rem] lg:px-[2rem] py-3 md:py-[0.625rem] lg:py-[0.875rem] rounded-full text-sm md:text-[0.875rem] lg:text-[1rem] font-medium transition-colors outline-none focus-visible:ring-2 focus-visible:ring-primary w-fit">
            Skontaktuj się z nami
          </button>
        </div>
        
      </div>
      <hr class="border border-about/20 mb-10 md:my-[3.875rem]" />
      <div class="flex flex-col lg:flex-row justify-between items-start mb-16 md:mb-[3.75rem] gap-10 lg:gap-0">
        <ul class="flex flex-col md:flex-row items-start md:items-center gap-4 md:gap-[1.5rem] lg:gap-[2.5rem] text-sm md:text-[0.875rem] lg:text-[1rem]">
          <li><a href="#" class="hover:text-white transition-colors outline-none focus-visible:underline">Kontakt</a></li>
          <li><a href="#" class="hover:text-white transition-colors outline-none focus-visible:underline">Instagram</a></li>
          <li><a href="#" class="hover:text-white transition-colors outline-none focus-visible:underline">Facebook</a></li>
          <li><a href="#" class="hover:text-white transition-colors outline-none focus-visible:underline">LinkedIn</a></li>
        </ul>
        <div class="flex flex-col md:flex-row items-start md:items-center gap-4 md:gap-[1.5rem] lg:gap-[2.5rem] text-sm md:text-[0.875rem] lg:text-[1rem]">
          <a href="tel:000000000" class="hover:text-white transition-colors outline-none focus-visible:underline">000-000-000</a>
          <a href="mailto:giarddesign@kontakt.pl" class="hover:text-white transition-colors outline-none focus-visible:underline">giarddesign@kontakt.pl</a>
        </div>
        
      </div>
      <div class="flex flex-col md:flex-row justify-between items-start md:items-center gap-6 md:gap-0 text-sm md:text-[0.875rem] lg:text-[1rem]">
        
        <p>Prawa zastrzeżone © 2022</p>
        
        <div class="flex items-center gap-2">
          <span>made by</span>
          <a 
            href="https://adrespect.pl" 
            target="_blank" 
            rel="noopener noreferrer" 
            class="font-bold flex items-center hover:opacity-80 transition-opacity outline-none focus-visible:ring-2 focus-visible:ring-about rounded"
          >
            <img src="../assets/logo_adRespect.svg" alt="Logo firmy ogrodniczej" class="w-[115px] h-[19px] md:w-[7.1875rem] md:h-[1.1875rem]" />
          </a>
        </div>
        
      </div>

    </div>
  </footer>
</template>