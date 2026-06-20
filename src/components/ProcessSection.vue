<template>
  <section id="process" class="process-section" ref="rootRef">
    <div class="container">
      <div class="section-header centered">
        <span class="section-badge">How It Works</span>
        <h2 class="section-title" :class="['animate-up', isInView ? 'in-view' : '']">
          A Mind That <span class="gradient-text">Grows With You</span>
        </h2>
        <p class="section-sub" :class="['animate-up d1', isInView ? 'in-view' : '']">
          Companion is both hardware and software. The hardware gives each model
          dedicated compute to live and grow on. The software brings it all to life.
        </p>
      </div>

      <!-- Hardware anatomy callout -->
      <div class="hardware-callout" :class="['animate-up d2', isInView ? 'in-view' : '']">
        <div class="hw-part">
          <div class="hw-icon">
            <svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.6" stroke-linecap="round" stroke-linejoin="round">
              <rect x="2" y="3" width="20" height="14" rx="2"/>
              <line x1="8" y1="21" x2="16" y2="21"/>
              <line x1="12" y1="17" x2="12" y2="21"/>
            </svg>
          </div>
          <div class="hw-copy">
            <h4>The Companion Base</h4>
            <p>The main unit that sits in your home. It connects to your home network and ties all AI cards together into one unified system.</p>
          </div>
        </div>
        <div class="hw-divider" aria-hidden="true">+</div>
        <div class="hw-part">
          <div class="hw-icon hw-icon--pink">
            <svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.6" stroke-linecap="round" stroke-linejoin="round">
              <rect x="4" y="2" width="16" height="20" rx="2"/>
              <line x1="8" y1="6" x2="16" y2="6"/>
              <line x1="8" y1="10" x2="16" y2="10"/>
              <line x1="8" y1="14" x2="12" y2="14"/>
            </svg>
          </div>
          <div class="hw-copy">
            <h4>AI Cards</h4>
            <p>One card per family member. Each card contains a dedicated multicore GPU that runs that person's model and handles all of its training — independently, in parallel with every other card in the base.</p>
          </div>
        </div>
      </div>

      <div class="steps-wrapper">
        <div class="steps">
          <div
            v-for="(step, i) in steps"
            :key="step.title"
            class="step"
            :class="['animate-up', isInView ? 'in-view' : '', `d${i + 1}`]"
          >
            <div class="step-number" :style="{ background: step.numBg }">
              <span>{{ String(i + 1).padStart(2, '0') }}</span>
            </div>
            <div class="step-icon" v-html="step.icon"/>
            <h3 class="step-title">{{ step.title }}</h3>
            <p class="step-desc">{{ step.desc }}</p>
            <div class="step-duration">{{ step.duration }}</div>
          </div>
        </div>
      </div>

      <!-- Retraining cycle visual note -->
      <div class="cycle-note" :class="['animate-up d5', isInView ? 'in-view' : '']">
        <div class="cycle-label">The Monthly Cycle</div>
        <div class="cycle-flow">
          <div class="cycle-step">
            <span class="cycle-dot purple"/>
            <span>Context builds</span>
          </div>
          <div class="cycle-arrow">→</div>
          <div class="cycle-step">
            <span class="cycle-dot violet"/>
            <span>Month closes</span>
          </div>
          <div class="cycle-arrow">→</div>
          <div class="cycle-step">
            <span class="cycle-dot pink"/>
            <span>Each card retrains its model</span>
          </div>
          <div class="cycle-arrow">→</div>
          <div class="cycle-step">
            <span class="cycle-dot purple"/>
            <span>A deeper person emerges</span>
          </div>
        </div>
        <p class="cycle-desc">
          Unlike cloud AI that treats every conversation as isolated, Companion's retraining loop
          means your models don't just remember — they <em>integrate</em>. Every cycle, each model becomes
          a more accurate reflection of the person it belongs to. And because every card has its own
          dedicated GPU, retraining happens simultaneously for every family member, with no card
          ever waiting on another.
        </p>
      </div>
    </div>
  </section>
</template>

<script setup>
import { useInView } from '../composables/useInView.js'

const { rootRef, isInView } = useInView()

const steps = [
  {
    title: 'Unbox & Connect the Base',
    desc: 'Plug the Companion Base into your home network. This is the hub that will coordinate every AI card in your family. It does not need the internet to operate — only your home network, when you are in the house. Power on and it is ready within minutes.',
    duration: '~5 minutes',
    numBg: 'linear-gradient(135deg, rgba(99,102,246,0.18), rgba(99,102,246,0.06))',
    icon: `<svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.6" stroke-linecap="round" stroke-linejoin="round"><rect x="2" y="3" width="20" height="14" rx="2"/><line x1="8" y1="21" x2="16" y2="21"/><line x1="12" y1="17" x2="12" y2="21"/></svg>`,
  },
  {
    title: 'Slot In Your First AI Card',
    desc: 'Each family member comes with their own AI card. Slide it into an open slot on the Companion Base. Then open the Companion app and run the setup to initialize that person\'s model on their card. The model awakens on dedicated hardware — a multicore GPU that belongs to them alone — and begins learning from day one.',
    duration: 'Minutes per card',
    numBg: 'linear-gradient(135deg, rgba(139,92,246,0.18), rgba(139,92,246,0.06))',
    icon: `<svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.6" stroke-linecap="round" stroke-linejoin="round"><rect x="4" y="2" width="16" height="20" rx="2"/><line x1="8" y1="6" x2="16" y2="6"/><line x1="8" y1="10" x2="16" y2="10"/><line x1="8" y1="14" x2="12" y2="14"/></svg>`,
  },
  {
    title: 'Grow Your Family, Grow the System',
    desc: 'When a new family member joins — a newborn, a partner, a grandparent — order their AI card. Slot it into the base, open the Companion app, and run the update. Their model initializes fresh on its own dedicated GPU, entirely isolated from every other card. The base ties them all together; the cards keep them apart.',
    duration: 'Whenever you need',
    numBg: 'linear-gradient(135deg, rgba(236,72,153,0.18), rgba(236,72,153,0.06))',
    icon: `<svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.6" stroke-linecap="round" stroke-linejoin="round"><path d="M17 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2"/><circle cx="9" cy="7" r="4"/><line x1="19" y1="8" x2="19" y2="14"/><line x1="22" y1="11" x2="16" y2="11"/></svg>`,
  },
  {
    title: 'Your Models Learn',
    desc: 'Day by day, each card\'s model builds a living picture of the person it belongs to. At month\'s end, each card runs a full retraining cycle on its own GPU — no card waits on another, no model ever touches another person\'s data. They grow in parallel, in silence, each becoming more itself.',
    duration: 'Every month, forever',
    numBg: 'linear-gradient(135deg, rgba(99,102,241,0.18), rgba(236,72,153,0.06))',
    icon: `<svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.6" stroke-linecap="round" stroke-linejoin="round"><polyline points="23 4 23 10 17 10"/><polyline points="1 20 1 14 7 14"/><path d="M3.51 9a9 9 0 0 1 14.85-3.36L23 10M1 14l4.64 4.36A9 9 0 0 0 20.49 15"/></svg>`,
  },
]
</script>

<style scoped>
.process-section {
  padding: clamp(5rem, 10vw, 8rem) 0;
  position: relative;
}

.process-section::before {
  content: '';
  position: absolute;
  inset: 0;
  background: radial-gradient(ellipse 80% 60% at 50% 50%, rgba(99, 102, 241, 0.05) 0%, transparent 60%);
  pointer-events: none;
}

.section-header.centered {
  text-align: center;
  margin: 0 auto 3rem;
  max-width: 560px;
}

.section-header.centered .section-sub {
  margin: 0 auto;
}

/* Hardware anatomy callout */
.hardware-callout {
  display: grid;
  grid-template-columns: 1fr auto 1fr;
  align-items: center;
  gap: 1.5rem;
  background: var(--bg-card);
  border: 1px solid var(--border);
  border-radius: var(--radius-lg);
  padding: 2rem 2.5rem;
  margin-bottom: 3rem;
}

.hw-part {
  display: flex;
  align-items: flex-start;
  gap: 1.25rem;
}

.hw-icon {
  width: 48px;
  height: 48px;
  display: flex;
  align-items: center;
  justify-content: center;
  background: rgba(99, 102, 241, 0.1);
  border: 1px solid rgba(99, 102, 241, 0.2);
  border-radius: 12px;
  color: var(--purple-light);
  flex-shrink: 0;
}

.hw-icon--pink {
  background: rgba(236, 72, 153, 0.1);
  border-color: rgba(236, 72, 153, 0.2);
  color: var(--pink-light);
}

.hw-copy h4 {
  font-size: 0.95rem;
  font-weight: 700;
  color: var(--text);
  margin-bottom: 0.4rem;
  letter-spacing: -0.01em;
}

.hw-copy p {
  font-size: 0.85rem;
  color: var(--text-secondary);
  line-height: 1.65;
}

.hw-divider {
  font-size: 1.5rem;
  font-weight: 300;
  color: var(--text-muted);
  padding: 0 0.5rem;
  flex-shrink: 0;
}

/* Steps */
.steps-wrapper {
  position: relative;
  margin-bottom: 3rem;
}

.steps {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 1.5rem;
}

.step {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: 0;
  padding: 2rem;
  background: var(--bg-card);
  border: 1px solid var(--border);
  border-radius: var(--radius);
  position: relative;
  transition: border-color 0.25s ease, box-shadow 0.25s ease;
}

.step:hover {
  border-color: var(--border-hover);
  box-shadow: 0 16px 48px rgba(99, 102, 241, 0.1);
}

.step-number {
  width: 44px;
  height: 44px;
  border-radius: 12px;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 1.25rem;
  border: 1px solid rgba(99, 102, 241, 0.2);
  flex-shrink: 0;
}

.step-number span {
  font-size: 0.8rem;
  font-weight: 800;
  letter-spacing: 0.04em;
  background: linear-gradient(135deg, var(--purple-light), var(--pink-light));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.step-icon {
  color: var(--purple-light);
  margin-bottom: 1.25rem;
  opacity: 0.7;
}

.step-title {
  font-size: 1.25rem;
  font-weight: 800;
  letter-spacing: -0.02em;
  color: var(--text);
  margin-bottom: 0.75rem;
}

.step-desc {
  font-size: 0.88rem;
  color: var(--text-secondary);
  line-height: 1.7;
  flex: 1;
  margin-bottom: 1.25rem;
}

.step-duration {
  font-size: 0.75rem;
  font-weight: 600;
  color: var(--text-muted);
  background: rgba(255, 255, 255, 0.04);
  border: 1px solid rgba(255, 255, 255, 0.07);
  padding: 0.25em 0.75em;
  border-radius: 999px;
  letter-spacing: 0.04em;
  margin-top: auto;
}

/* Cycle note */
.cycle-note {
  background: var(--bg-card);
  border: 1px solid var(--border);
  border-radius: var(--radius-lg);
  padding: 2.25rem;
}

.cycle-label {
  font-size: 0.7rem;
  font-weight: 700;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--purple-light);
  margin-bottom: 1.25rem;
}

.cycle-flow {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  flex-wrap: wrap;
  margin-bottom: 1.5rem;
}

.cycle-step {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  font-size: 0.88rem;
  font-weight: 600;
  color: var(--text-secondary);
}

.cycle-dot {
  width: 8px;
  height: 8px;
  border-radius: 50%;
  flex-shrink: 0;
}

.cycle-dot.purple  { background: var(--purple); }
.cycle-dot.violet  { background: var(--violet); }
.cycle-dot.pink    { background: var(--pink); }

.cycle-arrow {
  color: var(--text-muted);
  font-size: 0.9rem;
}

.cycle-desc {
  font-size: 0.88rem;
  color: var(--text-secondary);
  line-height: 1.75;
  max-width: 72ch;
}

.cycle-desc em {
  font-style: italic;
  color: var(--text);
}

@media (max-width: 900px) {
  .hardware-callout {
    grid-template-columns: 1fr;
  }
  .hw-divider {
    display: none;
  }
  .steps {
    grid-template-columns: 1fr;
    gap: 1.25rem;
  }
}

@media (max-width: 600px) {
  .cycle-flow {
    flex-direction: column;
    align-items: flex-start;
  }
  .cycle-arrow { transform: rotate(90deg); }
}
</style>
