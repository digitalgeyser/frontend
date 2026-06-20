<template>
  <section id="products" class="products-section" ref="rootRef">
    <div class="container">
      <div class="section-header">
        <span class="section-badge">Products</span>
        <h2 class="section-title" :class="['animate-up', isInView ? 'in-view' : '']">
          Everything Your <span class="gradient-text">Family Needs</span>
        </h2>
        <p class="section-sub" :class="['animate-up d1', isInView ? 'in-view' : '']">
          Companion is a single, complete system — hardware, software, and a philosophy
          built around one simple truth: every person deserves an AI that is truly theirs.
        </p>
      </div>

      <div class="products-grid">
        <div
          v-for="(product, i) in products"
          :key="product.title"
          class="product-card card"
          :class="['animate-up', isInView ? 'in-view' : '', `d${i + 1}`, { 'product-card--wide': product.wide }]"
        >
          <div class="product-icon" :style="{ background: product.iconBg }">
            <span v-html="product.icon"/>
          </div>
          <h3 class="product-title">{{ product.title }}</h3>
          <p class="product-desc">{{ product.desc }}</p>
          <div class="product-tags">
            <span v-for="tag in product.tags" :key="tag" class="tag">{{ tag }}</span>
          </div>
        </div>
      </div>

      <!-- Paradigm callout -->
      <div class="paradigm-callout" :class="['animate-up d4', isInView ? 'in-view' : '']">
        <div class="paradigm-inner">
          <div class="paradigm-icon" aria-hidden="true">
            <svg width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round">
              <path d="M20.84 4.61a5.5 5.5 0 0 0-7.78 0L12 5.67l-1.06-1.06a5.5 5.5 0 0 0-7.78 7.78l1.06 1.06L12 21.23l7.78-7.78 1.06-1.06a5.5 5.5 0 0 0 0-7.78z"/>
            </svg>
          </div>
          <div class="paradigm-copy">
            <h3>A Mind of Their Own — for Everyone</h3>
            <p>
              Imagine giving every person in your family a mind that is entirely their own — one that
              remembers, understands, and grows alongside them for as long as they live.
              Not just for children. For everyone.
              <strong>One model. One person. A lifetime of knowing.</strong>
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

const products = [
  {
    title: 'Companion Unit',
    desc: 'A compact, silent home server that runs your family\'s AI models entirely at home. The model does not need the internet to operate — it only needs your home network when you are in the house. Just plug in and it lives quietly on your shelf, always on.',
    icon: `<svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.6" stroke-linecap="round" stroke-linejoin="round"><rect x="2" y="3" width="20" height="14" rx="2"/><line x1="8" y1="21" x2="16" y2="21"/><line x1="12" y1="17" x2="12" y2="21"/></svg>`,
    iconBg: 'rgba(99, 102, 241, 0.12)',
    tags: ['Home Hardware', 'Local AI', 'Always-On'],
  },
  {
    title: 'A Model for Every Person',
    desc: 'Register any family member — a newborn, a teenager, a grandparent — through the Companion app and initialize their personal model. From that moment forward, the model is theirs: listening, learning, and remembering. The earlier it begins, the deeper it grows. But it is never too late to start.',
    icon: `<svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.6" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><path d="M12 8v4l3 3"/></svg>`,
    iconBg: 'rgba(139, 92, 246, 0.12)',
    tags: ['Gifting', 'Birth Registration', 'Lifelong'],
  },
  {
    title: 'Living Memory Engine',
    desc: 'Every month, each model\'s accumulated context — every conversation, question, and memory — becomes fresh training data. The models retrain on that lived experience, folding it into their core. They don\'t just remember; each evolves into a deeper version of itself.',
    icon: `<svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.6" stroke-linecap="round" stroke-linejoin="round"><polyline points="23 4 23 10 17 10"/><polyline points="1 20 1 14 7 14"/><path d="M3.51 9a9 9 0 0 1 14.85-3.36L23 10M1 14l4.64 4.36A9 9 0 0 0 20.49 15"/></svg>`,
    iconBg: 'rgba(236, 72, 153, 0.12)',
    tags: ['Self-Training', 'Context Loop', 'Continuous Evolution'],
  },
  {
    title: 'Family Hub',
    desc: 'One Companion Unit supports your entire household — up to six family members, each with their own completely isolated model. Models never share data, never interact, never mix. Every person in your family has an AI that knows only them.',
    icon: `<svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.6" stroke-linecap="round" stroke-linejoin="round"><path d="M17 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2"/><circle cx="9" cy="7" r="4"/><path d="M23 21v-2a4 4 0 0 0-3-3.87"/><path d="M16 3.13a4 4 0 0 1 0 7.75"/></svg>`,
    iconBg: 'rgba(244, 114, 182, 0.12)',
    tags: ['Multi-Model', 'Family Privacy', 'Isolated Profiles'],
    wide: false,
  },
  {
    title: 'Companion on the Road',
    desc: 'Your models live at home — but you don\'t have to. When you travel, the Companion app connects you to your home model through a secure cloud proxy. Your models stay where they belong; the proxy simply carries your voice to the right one and brings its response back. From your phone or laptop, anywhere in the world, it is still the same model — the one that knows you.',
    icon: `<svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.6" stroke-linecap="round" stroke-linejoin="round"><path d="M12 2C8.13 2 5 5.13 5 9c0 5.25 7 13 7 13s7-7.75 7-13c0-3.87-3.13-7-7-7z"/><circle cx="12" cy="9" r="2.5"/></svg>`,
    iconBg: 'rgba(99, 102, 241, 0.10)',
    tags: ['Cloud Proxy', 'Mobile App', 'Travel-Ready', 'Always Reachable'],
    wide: true,
  },
]
</script>

<style scoped>
.products-section {
  padding: clamp(5rem, 10vw, 8rem) 0;
  position: relative;
}

.section-header {
  max-width: 560px;
  margin-bottom: 3.5rem;
}

.products-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 1.5rem;
  margin-bottom: 2.5rem;
}

.product-card {
  padding: 2.25rem;
  display: flex;
  flex-direction: column;
  gap: 0;
}

.product-card--wide {
  grid-column: 1 / -1;
  flex-direction: row;
  align-items: flex-start;
  gap: 2rem;
}

.product-card--wide .product-icon {
  flex-shrink: 0;
  margin-bottom: 0;
}

.product-card--wide .product-desc {
  margin-bottom: 1.25rem;
}

.product-icon {
  width: 52px;
  height: 52px;
  border-radius: 14px;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 1.25rem;
  color: var(--purple-light);
  flex-shrink: 0;
  border: 1px solid rgba(99, 102, 241, 0.18);
}

.product-title {
  font-size: 1.1rem;
  font-weight: 700;
  color: var(--text);
  margin-bottom: 0.75rem;
  letter-spacing: -0.01em;
}

.product-desc {
  font-size: 0.9rem;
  color: var(--text-secondary);
  line-height: 1.7;
  flex: 1;
  margin-bottom: 1.5rem;
}

.product-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.4rem;
  margin-top: auto;
}

.tag {
  font-size: 0.7rem;
  font-weight: 600;
  letter-spacing: 0.05em;
  padding: 0.25em 0.75em;
  background: rgba(99, 102, 241, 0.08);
  border: 1px solid rgba(99, 102, 241, 0.18);
  border-radius: 999px;
  color: var(--purple-light);
}

/* Paradigm callout */
.paradigm-callout {
  background: linear-gradient(135deg, rgba(99, 102, 241, 0.08) 0%, rgba(236, 72, 153, 0.06) 100%);
  border: 1px solid rgba(99, 102, 241, 0.22);
  border-radius: var(--radius-lg);
  padding: 2.5rem;
}

.paradigm-inner {
  display: flex;
  align-items: flex-start;
  gap: 1.75rem;
}

.paradigm-icon {
  width: 56px;
  height: 56px;
  display: flex;
  align-items: center;
  justify-content: center;
  background: rgba(236, 72, 153, 0.1);
  border: 1px solid rgba(236, 72, 153, 0.22);
  border-radius: 16px;
  color: var(--pink-light);
  flex-shrink: 0;
}

.paradigm-copy h3 {
  font-size: 1.2rem;
  font-weight: 800;
  letter-spacing: -0.02em;
  color: var(--text);
  margin-bottom: 0.75rem;
}

.paradigm-copy p {
  font-size: 0.95rem;
  color: var(--text-secondary);
  line-height: 1.75;
  max-width: 70ch;
}

.paradigm-copy strong {
  color: var(--text);
  font-weight: 700;
}

@media (max-width: 768px) {
  .products-grid {
    grid-template-columns: 1fr;
  }

  .product-card--wide {
    flex-direction: column;
    gap: 0;
  }

  .product-card--wide .product-icon {
    margin-bottom: 1.25rem;
  }
  .paradigm-inner {
    flex-direction: column;
    gap: 1.25rem;
  }
}
</style>
