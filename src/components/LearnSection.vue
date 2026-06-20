<template>
  <section id="learn" class="learn-section" ref="rootRef">
    <div class="container">
      <div class="section-header centered">
        <span class="section-badge">How It Learns</span>
        <h2 class="section-title" :class="['animate-up', isInView ? 'in-view' : '']">
          How Does Your Companion <span class="gradient-text">Learn?</span>
        </h2>
        <p class="section-sub" :class="['animate-up d1', isInView ? 'in-view' : '']">
          Most of your life is already digital. Your email, your calendar, your bills,
          your messages — the texture of who you are exists in data you already produce
          every day. Your companion does not need to observe you. It just needs permission
          to read what is already there.
        </p>
      </div>

      <div class="sources-grid" :class="['animate-up d2', isInView ? 'in-view' : '']">
        <div
          v-for="source in sources"
          :key="source.title"
          class="source-card card"
        >
          <div class="source-icon" :style="{ background: source.iconBg, borderColor: source.borderColor }">
            <span v-html="source.icon"/>
          </div>
          <h3 class="source-title">{{ source.title }}</h3>
          <p class="source-desc">{{ source.desc }}</p>
        </div>
      </div>

      <!-- Control callout -->
      <div class="control-callout" :class="['animate-up d3', isInView ? 'in-view' : '']">
        <div class="control-inner">
          <div class="control-icon" aria-hidden="true">
            <svg width="26" height="26" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round">
              <rect x="3" y="11" width="18" height="11" rx="2" ry="2"/>
              <path d="M7 11V7a5 5 0 0 1 10 0v4"/>
            </svg>
          </div>
          <div class="control-copy">
            <h3>You Are Always in Control</h3>
            <p>
              Each person configures their own companion independently. You choose which
              parts of your digital life to grant access to — nothing is connected without
              your explicit permission. You can add sources, remove them, or pause access
              at any time through the Companion app. Your companion learns exactly as much
              as you want it to, and no more.
            </p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { useInView } from '../composables/useInView.js'

const { rootRef, isInView } = useInView()

const sources = [
  {
    title: 'Email & Messages',
    desc: 'Your written communication reveals how you think, what you care about, and who matters to you. Your companion can read your correspondence to build a picture of your relationships and priorities.',
    icon: `<svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.6" stroke-linecap="round" stroke-linejoin="round"><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/><polyline points="22,6 12,13 2,6"/></svg>`,
    iconBg: 'rgba(99, 102, 241, 0.10)',
    borderColor: 'rgba(99, 102, 241, 0.22)',
  },
  {
    title: 'Calendar & Schedule',
    desc: 'Where you spend your time is who you are. Your appointments, routines, and commitments give your companion a map of your days and an understanding of how your life is structured.',
    icon: `<svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.6" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="4" width="18" height="18" rx="2" ry="2"/><line x1="16" y1="2" x2="16" y2="6"/><line x1="8" y1="2" x2="8" y2="6"/><line x1="3" y1="10" x2="21" y2="10"/></svg>`,
    iconBg: 'rgba(139, 92, 246, 0.10)',
    borderColor: 'rgba(139, 92, 246, 0.22)',
  },
  {
    title: 'Documents & Files',
    desc: 'Your notes, contracts, receipts, and records are the paper trail of your life. Access to your documents lets your companion understand your history, your work, and your decisions over time.',
    icon: `<svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.6" stroke-linecap="round" stroke-linejoin="round"><path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"/><polyline points="14 2 14 8 20 8"/><line x1="16" y1="13" x2="8" y2="13"/><line x1="16" y1="17" x2="8" y2="17"/><polyline points="10 9 9 9 8 9"/></svg>`,
    iconBg: 'rgba(236, 72, 153, 0.10)',
    borderColor: 'rgba(236, 72, 153, 0.22)',
  },
  {
    title: 'Bills & Finances',
    desc: 'Your spending patterns reflect your values, your responsibilities, and your circumstances. Financial data gives your companion a grounded sense of how your life actually operates day to day.',
    icon: `<svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.6" stroke-linecap="round" stroke-linejoin="round"><line x1="12" y1="1" x2="12" y2="23"/><path d="M17 5H9.5a3.5 3.5 0 0 0 0 7h5a3.5 3.5 0 0 1 0 7H6"/></svg>`,
    iconBg: 'rgba(244, 114, 182, 0.10)',
    borderColor: 'rgba(244, 114, 182, 0.22)',
  },
  {
    title: 'Photos & Memories',
    desc: 'The moments you chose to capture tell a story words cannot. With access to your photos, your companion can understand what you have lived through and what has mattered enough to remember.',
    icon: `<svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.6" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="3" width="18" height="18" rx="2" ry="2"/><circle cx="8.5" cy="8.5" r="1.5"/><polyline points="21 15 16 10 5 21"/></svg>`,
    iconBg: 'rgba(99, 102, 241, 0.10)',
    borderColor: 'rgba(99, 102, 241, 0.22)',
  },
  {
    title: 'Health & Activity',
    desc: 'Sleep, movement, and physical patterns shape how you feel and how you think. Health data gives your companion a window into the rhythms of your body alongside the rhythms of your life.',
    icon: `<svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.6" stroke-linecap="round" stroke-linejoin="round"><polyline points="22 12 18 12 15 21 9 3 6 12 2 12"/></svg>`,
    iconBg: 'rgba(139, 92, 246, 0.10)',
    borderColor: 'rgba(139, 92, 246, 0.22)',
  },
]
</script>

<style scoped>
.learn-section {
  padding: clamp(5rem, 10vw, 8rem) 0;
  position: relative;
}

.learn-section::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 1px;
  background: linear-gradient(90deg, transparent, rgba(99, 102, 241, 0.25), transparent);
}

.section-header.centered {
  text-align: center;
  margin: 0 auto 3.5rem;
  max-width: 640px;
}

.section-header.centered .section-sub {
  margin: 0 auto;
}

.sources-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1.25rem;
  margin-bottom: 2.5rem;
}

.source-card {
  padding: 1.75rem;
  display: flex;
  flex-direction: column;
  gap: 0;
}

.source-icon {
  width: 48px;
  height: 48px;
  border-radius: 12px;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 1.1rem;
  border: 1px solid;
  color: var(--purple-light);
  flex-shrink: 0;
}

.source-title {
  font-size: 0.97rem;
  font-weight: 700;
  color: var(--text);
  margin-bottom: 0.6rem;
  letter-spacing: -0.01em;
}

.source-desc {
  font-size: 0.85rem;
  color: var(--text-secondary);
  line-height: 1.7;
}

/* Control callout */
.control-callout {
  background: linear-gradient(135deg, rgba(99, 102, 241, 0.07) 0%, rgba(139, 92, 246, 0.05) 100%);
  border: 1px solid rgba(99, 102, 241, 0.2);
  border-radius: var(--radius-lg);
  padding: 2.5rem;
}

.control-inner {
  display: flex;
  align-items: flex-start;
  gap: 1.75rem;
}

.control-icon {
  width: 54px;
  height: 54px;
  display: flex;
  align-items: center;
  justify-content: center;
  background: rgba(99, 102, 241, 0.1);
  border: 1px solid rgba(99, 102, 241, 0.22);
  border-radius: 14px;
  color: var(--purple-light);
  flex-shrink: 0;
}

.control-copy h3 {
  font-size: 1.15rem;
  font-weight: 800;
  letter-spacing: -0.02em;
  color: var(--text);
  margin-bottom: 0.75rem;
}

.control-copy p {
  font-size: 0.95rem;
  color: var(--text-secondary);
  line-height: 1.75;
  max-width: 72ch;
}

@media (max-width: 900px) {
  .sources-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 600px) {
  .sources-grid {
    grid-template-columns: 1fr;
  }
  .control-inner {
    flex-direction: column;
    gap: 1.25rem;
  }
}
</style>
