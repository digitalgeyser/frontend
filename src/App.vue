<template>
  <div id="app">
    <NavBar />
    <main>
      <HeroSection />
      <AboutSection />
      <ServicesSection />
      <ResearchSection />
      <ProcessSection />
      <ContactSection />
    </main>
    <FooterSection />
  </div>
</template>

<script setup>
import NavBar from './components/NavBar.vue'
import HeroSection from './components/HeroSection.vue'
import AboutSection from './components/AboutSection.vue'
import ServicesSection from './components/ServicesSection.vue'
import ResearchSection from './components/ResearchSection.vue'
import ProcessSection from './components/ProcessSection.vue'
import ContactSection from './components/ContactSection.vue'
import FooterSection from './components/FooterSection.vue'
</script>
