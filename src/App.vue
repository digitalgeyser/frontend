<template>
  <div id="app">
    <NavBar />
    <main>
      <HeroSection />
      <AboutSection />
      <LearnSection />
      <ServicesSection />
      <ProcessSection />
      <CloudSection />
      <ContactSection />
    </main>
    <FooterSection />
  </div>
</template>

<script setup>
import NavBar from './components/NavBar.vue'
import HeroSection from './components/HeroSection.vue'
import AboutSection from './components/AboutSection.vue'
import LearnSection from './components/LearnSection.vue'
import ServicesSection from './components/ServicesSection.vue'
import ProcessSection from './components/ProcessSection.vue'
import CloudSection from './components/CloudSection.vue'
import ContactSection from './components/ContactSection.vue'
import FooterSection from './components/FooterSection.vue'
</script>
