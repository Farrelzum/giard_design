<script setup>
</script>

<template>
  <section class="w-full bg-about py-16 md:py-[4rem] lg:py-[6rem]">
    <div class="max-w-7xl mx-auto px-4">
      <div class="grid grid-cols-12">
        <div class="col-span-12 lg:col-span-10 lg:col-start-2 bg-primary flex flex-col md:flex-row items-start md:items-center justify-center gap-8 md:gap-[2rem] lg:gap-[4rem] p-8 md:p-[3rem] lg:p-[4.5rem]">
          <div class="mb-10 md:mb-0">
            <h2 class="text-3xl md:text-10 lg:text-10 md:leading-[1.2] text-about">
              Zostańmy w kontakcie!<br />
              Znajdziesz nas na <span class="italic">Instagramie</span>.
            </h2>
          </div>
          <div class="flex flex-col items-start">
            <p class="text-about text-sm md:text-[1rem] md:leading-[1.5rem] mb-4 md:mb-[1.5rem]">
              Śledź nasze <br class="hidden md:block" /> najnowsze realizacje!
            </p>
            <!-- NA TO: -->
            <a 
            href="https://www.instagram.com/adrespect/" 
            target="_blank" 
            rel="noopener noreferrer"
            class="inline-block bg-about text-primary hover:bg-white px-8 md:px-[2rem] py-3 md:py-[0.875rem] rounded-full text-sm md:text-[1rem] font-medium transition-colors outline-none focus-visible:ring-2 focus-visible:ring-white text-center"
            >
                Instagram
            </a>
          </div>
          
        </div>
        
      </div>
      
    </div>
  </section>
</template>