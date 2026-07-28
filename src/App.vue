<script setup>
import TheNavbar from './components/TheNavbar.vue'
import HeroSlider from './components/HeroSlider.vue'
import OfferSection from './components/OfferSection.vue';
import AboutSection from './components/AboutSection.vue';
import ProjectsSection from './components/ProjectsSection.vue';
import InstagramSection from './components/InstagramSection.vue';
import FooterSection from './components/FooterSection.vue';
</script>

<template>
  <div class="font-body min-h-screen">
    <TheNavbar />
    <main>
      <HeroSlider />
      <OfferSection />
      <AboutSection />
      <ProjectsSection />
      <InstagramSection />
      <FooterSection />
    </main>
  </div>
</template>