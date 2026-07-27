<script setup>
import TheNavbar from './components/TheNavbar.vue'
import HeroSlider from './components/HeroSlider.vue'
import OfferSection from './components/OfferSection.vue';
</script>

<template>
  <div class="font-body min-h-screen">
    <TheNavbar />
    <main>
      <HeroSlider />
      <OfferSection />
    </main>
  </div>
</template>