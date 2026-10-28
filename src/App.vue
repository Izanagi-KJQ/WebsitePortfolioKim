<template>
  <div id="app">
    <NavBar />

    <main>
      <HeroSection />

      <div class="section-separator">
        <div class="separator-line"></div>
      </div>

      <WorksSection />

      <div class="section-separator">
        <div class="separator-line"></div>
      </div>

      <AboutSection />

      <div class="section-separator">
        <div class="separator-line"></div>
      </div>

      <ProcessSection />

      <div class="section-separator">
        <div class="separator-line"></div>
      </div>

      <TestimonialsSection />
    </main>

    <FooterCTA />
  </div>
</template>

<script setup>
import NavBar from './components/NavBar.vue'
import HeroSection from './components/HeroSection.vue'
import WorksSection from './components/WorksSection.vue'
import AboutSection from './components/AboutSection.vue'
import ProcessSection from './components/ProcessSection.vue'
import TestimonialsSection from './components/TestimonialsSection.vue'
import FooterCTA from './components/FooterCTA.vue'
</script>

<style>
.section-separator {
  display: flex;
  justify-content: center;
  padding: 0 2rem;
}

.separator-line {
  max-width: 1200px;
  width: 100%;
  height: 1px;
  background: linear-gradient(to right, transparent, rgba(255,255,255,0.06), transparent);
}
</style>
