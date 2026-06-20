<template>
  <section id="contact" class="contact-section" ref="rootRef">
    <div class="container">
      <div class="contact-card">
        <div class="card-glow" aria-hidden="true"/>

        <div class="contact-inner" :class="['animate-up', isInView ? 'in-view' : '']">
          <div class="contact-copy">
            <span class="section-badge">How Can I Get One?</span>
            <h2 class="section-title">
              Coming <span class="gradient-text">Soon</span>
            </h2>
            <p class="section-sub">
              Companion — both the hardware and the software — is currently in development.
              We are working hard to bring it to families as soon as possible.
              If you would like to be notified when it becomes available, reach out and we
              will make sure you are among the first to know.
            </p>
          </div>

          <div class="contact-cta">
            <p class="cta-label">Get in touch at</p>
            <a href="mailto:info@digitalgeyser.com" class="email-link">
              <div class="email-icon">
                <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/><polyline points="22,6 12,13 2,6"/></svg>
              </div>
              info@digitalgeyser.com
            </a>
            <p class="response-note">We respond within 24 hours.</p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { useInView } from '../composables/useInView.js'

const { rootRef, isInView } = useInView()
</script>

<style scoped>
.contact-section {
  padding: clamp(5rem, 10vw, 8rem) 0;
}

.contact-card {
  background: var(--bg-card);
  border: 1px solid var(--border);
  border-radius: var(--radius-lg);
  padding: 3.5rem;
  position: relative;
  overflow: hidden;
}

.card-glow {
  position: absolute;
  top: -60px;
  right: -60px;
  width: 400px;
  height: 400px;
  background: radial-gradient(ellipse, rgba(99, 102, 241, 0.12) 0%, rgba(236, 72, 153, 0.06) 50%, transparent 70%);
  pointer-events: none;
  border-radius: 50%;
}

.contact-inner {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 4rem;
  align-items: center;
  position: relative;
  z-index: 1;
}

.contact-copy {
  padding-top: 0.5rem;
}

.contact-cta {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.cta-label {
  font-size: 0.85rem;
  color: var(--text-muted);
  text-transform: uppercase;
  letter-spacing: 0.08em;
  font-weight: 600;
}

.email-link {
  display: inline-flex;
  align-items: center;
  gap: 0.75rem;
  font-size: 1.15rem;
  font-weight: 600;
  color: var(--purple-light);
  text-decoration: none;
  transition: opacity 0.2s;
}

.email-link:hover {
  opacity: 0.8;
}

.email-icon {
  width: 40px;
  height: 40px;
  display: flex;
  align-items: center;
  justify-content: center;
  background: rgba(99, 102, 241, 0.1);
  border: 1px solid rgba(99, 102, 241, 0.2);
  border-radius: 10px;
  color: var(--purple-light);
  flex-shrink: 0;
}

.response-note {
  font-size: 0.85rem;
  color: var(--text-muted);
}

@media (max-width: 900px) {
  .contact-inner {
    grid-template-columns: 1fr;
    gap: 2.5rem;
  }
  .contact-card {
    padding: 2.25rem;
  }
}
</style>
