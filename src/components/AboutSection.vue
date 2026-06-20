<template>
  <section id="about" class="about-section" ref="rootRef">
    <div class="container">
      <div class="about-grid">
        <!-- Left: copy -->
        <div class="about-copy">
          <span class="section-badge">About</span>
          <h2 class="section-title" :class="['animate-up', isInView ? 'in-view' : '']">
            One Model.<br>
            <span class="gradient-text">One Person. Forever.</span>
          </h2>
          <p class="section-sub" :class="['animate-up d1', isInView ? 'in-view' : '']">
            Every AI you've ever used forgets you the moment you close the tab.
            Digital Geyser believes in something else: every person deserves an AI
            that actually knows them — not a generic assistant, but a mind
            that has grown alongside them and remembers who they are.
          </p>
          <p class="section-sub about-p2" :class="['animate-up d2', isInView ? 'in-view' : '']">
            Companion is a home server that runs private, dedicated AI models for each
            family member — one model per person, never shared. The models stay at home.
            They do not need the internet to operate, only your home network when you
            are in the house. When you travel, a secure cloud proxy carries your
            conversation to your home model and brings its response back, so you can
            reach it from your phone or laptop wherever you are. Just a quiet box on
            your shelf, holding intelligences that are entirely, irreversibly theirs —
            each building context month by month, retraining on lived experience, and
            becoming more deeply personal with every passing year.
          </p>
        </div>

        <!-- Right: stats -->
        <div class="stats-grid" :class="['animate-up d2', isInView ? 'in-view' : '']">
          <div class="stat-card card" v-for="stat in stats" :key="stat.label">
            <div class="stat-value">
              <span class="gradient-text-accent">{{ stat.value }}</span>
            </div>
            <div class="stat-label">{{ stat.label }}</div>
            <div class="stat-desc">{{ stat.desc }}</div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { useInView } from '../composables/useInView.js'

const { rootRef, isInView } = useInView()

const stats = [
  { value: '1', label: 'Model Per Person', desc: 'Dedicated, private, and never shared — even within a family' },
  { value: '~30d', label: 'Retraining Cycle', desc: 'Context built over a month becomes the next evolution of each model' },
  { value: '100%', label: 'On-Device', desc: 'Models stay at home. They only need your home network to run — no internet required' },
  { value: '∞', label: 'Lifelong Growth', desc: 'The sooner it starts, the deeper it grows — but it is never too late to begin' },
]
</script>

<style scoped>
.about-section {
  padding: clamp(5rem, 10vw, 8rem) 0;
  position: relative;
}

.about-section::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 1px;
  background: linear-gradient(90deg, transparent, rgba(99, 102, 241, 0.25), transparent);
}

.about-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 5rem;
  align-items: center;
}

.about-copy {
  max-width: 520px;
}

.about-p2 {
  margin-top: 1rem;
  transition-delay: 0.25s;
}

.stats-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1.25rem;
}

.stat-card {
  padding: 1.75rem;
  position: relative;
  overflow: hidden;
}

.stat-card::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  height: 2px;
  background: linear-gradient(90deg, var(--purple), var(--pink));
  opacity: 0;
  transition: opacity 0.3s ease;
}

.stat-card:hover::after {
  opacity: 1;
}

.stat-value {
  font-size: 2.2rem;
  font-weight: 900;
  letter-spacing: -0.04em;
  line-height: 1;
  margin-bottom: 0.5rem;
}

.stat-label {
  font-size: 0.88rem;
  font-weight: 600;
  color: var(--text);
  margin-bottom: 0.35rem;
}

.stat-desc {
  font-size: 0.78rem;
  color: var(--text-muted);
  line-height: 1.5;
}

@media (max-width: 900px) {
  .about-grid {
    grid-template-columns: 1fr;
    gap: 3rem;
  }
  .about-copy {
    max-width: none;
  }
}

@media (max-width: 480px) {
  .stats-grid {
    grid-template-columns: 1fr;
  }
}
</style>
