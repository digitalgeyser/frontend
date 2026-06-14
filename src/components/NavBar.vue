<template>
  <header :class="['navbar', { scrolled }]">
    <div class="container nav-inner">
      <!-- Logo -->
      <a href="#hero" class="logo" @click.prevent="scrollTo('hero')">
        <svg width="30" height="30" viewBox="0 0 30 30" fill="none" aria-hidden="true">
          <circle cx="15" cy="22" r="5" stroke="url(#ng)" stroke-width="1.5" fill="none"/>
          <line x1="15" y1="17" x2="15" y2="4" stroke="url(#ng)" stroke-width="2" stroke-linecap="round"/>
          <line x1="13.5" y1="11" x2="8" y2="5" stroke="#a5b4fc" stroke-width="1.5" stroke-linecap="round" opacity="0.7"/>
          <line x1="16.5" y1="11" x2="22" y2="5" stroke="#f472b6" stroke-width="1.5" stroke-linecap="round" opacity="0.7"/>
          <circle cx="15" cy="3" r="1.8" fill="url(#ng)"/>
          <circle cx="7" cy="4.5" r="1.1" fill="#a5b4fc" opacity="0.6"/>
          <circle cx="23" cy="4.5" r="1.1" fill="#f472b6" opacity="0.6"/>
          <defs>
            <linearGradient id="ng" x1="0" y1="1" x2="0" y2="0" gradientUnits="objectBoundingBox">
              <stop offset="0%" stop-color="#6366f1"/>
              <stop offset="100%" stop-color="#ec4899"/>
            </linearGradient>
          </defs>
        </svg>
        <span class="logo-text">Digital <span class="logo-accent">Geyser</span></span>
      </a>

      <!-- Desktop nav -->
      <nav class="desktop-nav">
        <a v-for="link in links" :key="link.id" href="#" @click.prevent="scrollTo(link.id)">{{ link.label }}</a>
      </nav>

      <div class="nav-cta">
        <a href="#contact" class="btn-primary" @click.prevent="scrollTo('contact')">Get in Touch</a>
        <button class="hamburger" :class="{ open: menuOpen }" @click="toggleMenu" aria-label="Toggle menu">
          <span/><span/><span/>
        </button>
      </div>
    </div>

    <!-- Mobile menu -->
    <div class="mobile-menu" :class="{ open: menuOpen }">
      <a v-for="link in links" :key="link.id" href="#" @click.prevent="scrollTo(link.id)">{{ link.label }}</a>
      <a href="#contact" class="btn-primary mobile-cta" @click.prevent="scrollTo('contact')">Get in Touch</a>
    </div>
  </header>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const scrolled = ref(false)
const menuOpen = ref(false)

const links = [
  { id: 'about', label: 'About' },
  { id: 'services', label: 'Services' },
  { id: 'process', label: 'Process' },
]

function onScroll() {
  scrolled.value = window.scrollY > 60
}

function toggleMenu() {
  menuOpen.value = !menuOpen.value
}

function scrollTo(id) {
  menuOpen.value = false
  document.getElementById(id)?.scrollIntoView({ behavior: 'smooth' })
}

onMounted(() => window.addEventListener('scroll', onScroll, { passive: true }))
onUnmounted(() => window.removeEventListener('scroll', onScroll))
</script>

<style scoped>
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 100;
  padding: 1.1rem 0;
  transition: background 0.3s ease, box-shadow 0.3s ease, padding 0.3s ease;
}

.navbar.scrolled {
  background: rgba(15, 15, 19, 0.88);
  backdrop-filter: blur(16px);
  -webkit-backdrop-filter: blur(16px);
  box-shadow: 0 1px 0 rgba(99, 102, 241, 0.12);
  padding: 0.75rem 0;
}

.nav-inner {
  display: flex;
  align-items: center;
  gap: 2rem;
}

/* Logo */
.logo {
  display: flex;
  align-items: center;
  gap: 0.6rem;
  font-size: 1.05rem;
  font-weight: 700;
  color: var(--text);
  flex-shrink: 0;
}

.logo-text {
  letter-spacing: -0.01em;
}

.logo-accent {
  background: linear-gradient(135deg, #a5b4fc, #f472b6);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

/* Desktop nav */
.desktop-nav {
  display: flex;
  align-items: center;
  gap: 0.25rem;
  flex: 1;
}

.desktop-nav a {
  font-size: 0.88rem;
  font-weight: 500;
  color: var(--text-secondary);
  padding: 0.4em 0.85em;
  border-radius: 999px;
  transition: color 0.2s, background 0.2s;
}

.desktop-nav a:hover {
  color: var(--text);
  background: rgba(255, 255, 255, 0.06);
}

/* CTA area */
.nav-cta {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  margin-left: auto;
}

/* Hamburger */
.hamburger {
  display: none;
  flex-direction: column;
  justify-content: center;
  gap: 5px;
  width: 36px;
  height: 36px;
  background: none;
  border: none;
  cursor: pointer;
  padding: 6px;
  border-radius: 8px;
  transition: background 0.2s;
}

.hamburger:hover {
  background: rgba(255, 255, 255, 0.07);
}

.hamburger span {
  display: block;
  height: 1.5px;
  background: var(--text-secondary);
  border-radius: 999px;
  transition: transform 0.3s ease, opacity 0.3s ease, width 0.3s ease;
  transform-origin: center;
}

.hamburger.open span:nth-child(1) { transform: translateY(6.5px) rotate(45deg); }
.hamburger.open span:nth-child(2) { opacity: 0; }
.hamburger.open span:nth-child(3) { transform: translateY(-6.5px) rotate(-45deg); }

/* Mobile menu */
.mobile-menu {
  display: none;
  flex-direction: column;
  padding: 0.5rem 1.5rem 1.25rem;
  gap: 0.25rem;
  background: rgba(13, 13, 20, 0.96);
  backdrop-filter: blur(16px);
  -webkit-backdrop-filter: blur(16px);
  border-top: 1px solid rgba(99, 102, 241, 0.1);
  overflow: hidden;
  max-height: 0;
  transition: max-height 0.35s ease, padding 0.35s ease;
}

.mobile-menu.open {
  max-height: 400px;
}

.mobile-menu a {
  font-size: 1rem;
  font-weight: 500;
  color: var(--text-secondary);
  padding: 0.6rem 0;
  border-bottom: 1px solid rgba(255, 255, 255, 0.05);
  transition: color 0.2s;
}

.mobile-menu a:hover {
  color: var(--text);
}

.mobile-cta {
  margin-top: 0.75rem;
  align-self: flex-start;
  border-bottom: none !important;
}

@media (max-width: 768px) {
  .desktop-nav { display: none; }
  .hamburger { display: flex; }
  .mobile-menu { display: flex; }
  .nav-cta .btn-primary { display: none; }
}
</style>
