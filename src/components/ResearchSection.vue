<template>
  <section id="research" class="research-section" ref="rootRef">
    <div class="container">
      <div class="section-header">
        <span class="section-badge">Research</span>
        <h2 class="section-title" :class="['animate-up', isInView ? 'in-view' : '']">
          Our Latest <span class="gradient-text">Work</span>
        </h2>
        <p class="section-sub" :class="['animate-up d1', isInView ? 'in-view' : '']">
          We publish openly. Our research spans language models, safety, multi-agent systems,
          and applied domain adaptation — always bridging theory and practice.
        </p>
      </div>

      <div class="papers-grid">
        <article
          v-for="(paper, i) in papers"
          :key="paper.title"
          class="paper-card card"
          :class="['animate-up', isInView ? 'in-view' : '', `d${i + 1}`]"
        >
          <div class="paper-meta">
            <span class="paper-year">{{ paper.year }}</span>
            <div class="paper-venue">{{ paper.venue }}</div>
          </div>
          <h3 class="paper-title">{{ paper.title }}</h3>
          <p class="paper-abstract">{{ paper.abstract }}</p>
          <div class="paper-footer">
            <div class="paper-tags">
              <span v-for="tag in paper.tags" :key="tag" class="tag">{{ tag }}</span>
            </div>
            <a href="#" class="paper-link" @click.prevent>
              Read paper
              <svg width="12" height="12" viewBox="0 0 12 12" fill="none" aria-hidden="true">
                <path d="M1 6h10M7 2l4 4-4 4" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
              </svg>
            </a>
          </div>
        </article>
      </div>
    </div>
  </section>
</template>

<script setup>
import { useInView } from '../composables/useInView.js'

const { rootRef, isInView } = useInView()

const papers = [
  {
    year: '2025',
    venue: 'NeurIPS 2025',
    title: 'Sparse Attention for Enterprise Long-Context Reasoning',
    abstract: 'We introduce a sparse attention pattern that reduces memory complexity for long-context reasoning by 3.7× while preserving 98% of benchmark accuracy on enterprise workloads.',
    tags: ['NLP', 'Transformers', 'Efficiency'],
  },
  {
    year: '2024',
    venue: 'ICLR 2024',
    title: 'Calibrated Uncertainty in High-Stakes AI Deployment',
    abstract: 'A framework for deploying ML models where calibrated confidence is as critical as raw accuracy, with case studies from medical imaging and financial risk assessment.',
    tags: ['Safety', 'Healthcare AI', 'Deployment'],
  },
  {
    year: '2024',
    venue: 'ICML 2024',
    title: 'Multi-Agent Coordination Under Communication Constraints',
    abstract: 'We study how multi-agent systems achieve near-optimal coordination under severe bandwidth limits, demonstrating applications in autonomous logistics and robotics.',
    tags: ['Multi-Agent', 'Optimization', 'Robotics'],
  },
  {
    year: '2023',
    venue: 'ACL 2023',
    title: 'Domain-Adaptive Fine-Tuning Without Catastrophic Forgetting',
    abstract: 'AdaptNet: a continual learning technique for domain adaptation that preserves general-purpose capability while achieving state-of-the-art results on specialized domains.',
    tags: ['Transfer Learning', 'NLP', 'Fine-tuning'],
  },
]
</script>

<style scoped>
.research-section {
  padding: clamp(5rem, 10vw, 8rem) 0;
  position: relative;
}

.research-section::before {
  content: '';
  position: absolute;
  inset: 0;
  background: radial-gradient(ellipse 70% 50% at 80% 30%, rgba(99, 102, 241, 0.06) 0%, transparent 60%);
  pointer-events: none;
}

.section-header {
  max-width: 560px;
  margin-bottom: 3.5rem;
}

.papers-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 1.5rem;
}

.paper-card {
  padding: 2rem;
  display: flex;
  flex-direction: column;
  gap: 0;
}

.paper-meta {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 1rem;
}

.paper-year {
  font-size: 0.75rem;
  font-weight: 700;
  color: var(--purple-light);
  background: rgba(99, 102, 241, 0.1);
  border: 1px solid rgba(99, 102, 241, 0.22);
  padding: 0.2em 0.7em;
  border-radius: 999px;
}

.paper-venue {
  font-size: 0.75rem;
  color: var(--text-muted);
  font-weight: 500;
}

.paper-title {
  font-size: 1.05rem;
  font-weight: 700;
  color: var(--text);
  line-height: 1.4;
  letter-spacing: -0.015em;
  margin-bottom: 0.85rem;
}

.paper-abstract {
  font-size: 0.87rem;
  color: var(--text-secondary);
  line-height: 1.7;
  flex: 1;
  margin-bottom: 1.5rem;
}

.paper-footer {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 1rem;
  flex-wrap: wrap;
}

.paper-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.35rem;
}

.tag {
  font-size: 0.67rem;
  font-weight: 600;
  letter-spacing: 0.05em;
  padding: 0.22em 0.65em;
  background: rgba(99, 102, 241, 0.07);
  border: 1px solid rgba(99, 102, 241, 0.16);
  border-radius: 999px;
  color: var(--purple-light);
}

.paper-link {
  display: inline-flex;
  align-items: center;
  gap: 0.35rem;
  font-size: 0.82rem;
  font-weight: 600;
  color: var(--purple-light);
  transition: color 0.2s, gap 0.2s;
  flex-shrink: 0;
}

.paper-link:hover {
  color: var(--pink-light);
  gap: 0.5rem;
}

@media (max-width: 768px) {
  .papers-grid {
    grid-template-columns: 1fr;
  }
}
</style>
