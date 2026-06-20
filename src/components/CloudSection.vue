<template>
  <section id="cloud" class="cloud-section" ref="rootRef">
    <div class="container">
      <div class="section-header centered">
        <span class="section-badge">Cloud Services</span>
        <h2 class="section-title" :class="['animate-up', isInView ? 'in-view' : '']">
          Yours to Keep. <span class="gradient-text">Safe to Trust.</span>
        </h2>
        <p class="section-sub" :class="['animate-up d1', isInView ? 'in-view' : '']">
          Your model lives on your AI card. But the cloud is there when you need it —
          for backups, for transfers, for locks, and for the configuration that keeps
          everything running the way you want.
        </p>
      </div>

      <!-- Cloud services grid -->
      <div class="cloud-grid" :class="['animate-up d2', isInView ? 'in-view' : '']">
        <div v-for="service in cloudServices" :key="service.title" class="cloud-card card">
          <div class="cloud-icon" :style="{ background: service.iconBg, borderColor: service.borderColor }">
            <span v-html="service.icon"/>
          </div>
          <h3 class="cloud-title">{{ service.title }}</h3>
          <p class="cloud-desc">{{ service.desc }}</p>
        </div>
      </div>

      <!-- Cryptographic identity -->
      <div class="identity-callout" :class="['animate-up d3', isInView ? 'in-view' : '']">
        <div class="identity-inner">
          <div class="identity-icon" aria-hidden="true">
            <svg width="26" height="26" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round">
              <path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z"/>
            </svg>
          </div>
          <div class="identity-copy">
            <h3>Cryptographically Yours</h3>
            <p>
              Every model is cryptographically linked to a single person at initialization.
              An adult's companion is reachable only by that adult — no one else, not even
              within the same household. All communication between a person and their model
              is end-to-end encrypted at all times, whether they are at home on the local
              network or reaching it through the cloud proxy while traveling.
            </p>
          </div>
        </div>
      </div>

      <!-- Family access model -->
      <div class="family-access" :class="['animate-up d4', isInView ? 'in-view' : '']">
        <div class="family-access-header">
          <div class="family-access-label">Family Access Model</div>
          <h3 class="family-access-title">Access That Grows With the Person</h3>
          <p class="family-access-sub">
            Children's models are not locked away from parents — but they are not
            wide open either. Access is structured around trust, and trust is
            structured around age.
          </p>
        </div>
        <div class="access-tiers">
          <div v-for="tier in accessTiers" :key="tier.label" class="access-tier">
            <div class="tier-bar" :style="{ background: tier.color }"/>
            <div class="tier-copy">
              <div class="tier-label" :style="{ color: tier.labelColor }">{{ tier.label }}</div>
              <p class="tier-desc">{{ tier.desc }}</p>
            </div>
          </div>
        </div>
      </div>

      <!-- Portability callout -->
      <div class="portability-callout" :class="['animate-up d5', isInView ? 'in-view' : '']">
        <div class="portability-inner">
          <div class="portability-icon" aria-hidden="true">
            <svg width="26" height="26" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round">
              <rect x="4" y="2" width="16" height="20" rx="2"/>
              <line x1="8" y1="6" x2="16" y2="6"/>
              <line x1="8" y1="10" x2="16" y2="10"/>
              <line x1="8" y1="14" x2="12" y2="14"/>
            </svg>
          </div>
          <div class="portability-copy">
            <h3>The Model Is Where the Card Is</h3>
            <p>
              When a person leaves a household — going to university, moving out, starting
              their own life — they take their companion with them as simply as unplugging
              their AI card and walking out the door. The card connects to any Companion Base.
              Nothing is left behind. Nothing needs to be transferred. The model is the card,
              and the card belongs to them.
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

const cloudServices = [
  {
    title: 'Encrypted Backups',
    desc: 'Your model is periodically backed up to an encrypted cloud vault. If your AI card is ever lost, damaged, or replaced, your model — every cycle, every memory, every layer of growth — is restored exactly as it was.',
    icon: `<svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.6" stroke-linecap="round" stroke-linejoin="round"><polyline points="20 6 9 17 4 12"/><path d="M22 12A10 10 0 1 1 12 2"/></svg>`,
    iconBg: 'rgba(99, 102, 241, 0.10)',
    borderColor: 'rgba(99, 102, 241, 0.22)',
  },
  {
    title: 'Hardware Transfer',
    desc: 'Upgrading to a new Companion Base? Your AI card moves with you. When slotting into new hardware, the Companion app handles re-linking automatically. Your model does not notice the difference.',
    icon: `<svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.6" stroke-linecap="round" stroke-linejoin="round"><polyline points="17 1 21 5 17 9"/><path d="M3 11V9a4 4 0 0 1 4-4h14"/><polyline points="7 23 3 19 7 15"/><path d="M21 13v2a4 4 0 0 1-4 4H3"/></svg>`,
    iconBg: 'rgba(139, 92, 246, 0.10)',
    borderColor: 'rgba(139, 92, 246, 0.22)',
  },
  {
    title: 'Remote Lock',
    desc: 'If your AI card is lost or stolen, you can lock it instantly from the Companion app. A locked card becomes completely inaccessible — the model cannot be reached, read, or tampered with until you unlock it.',
    icon: `<svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.6" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="11" width="18" height="11" rx="2" ry="2"/><path d="M7 11V7a5 5 0 0 1 10 0v4"/></svg>`,
    iconBg: 'rgba(236, 72, 153, 0.10)',
    borderColor: 'rgba(236, 72, 153, 0.22)',
  },
  {
    title: 'Remote Configuration',
    desc: 'Manage data source permissions, access settings, firmware updates, and retraining schedules from the Companion app — whether you are at home or on the other side of the world.',
    icon: `<svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.6" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="3"/><path d="M19.4 15a1.65 1.65 0 0 0 .33 1.82l.06.06a2 2 0 0 1-2.83 2.83l-.06-.06a1.65 1.65 0 0 0-1.82-.33 1.65 1.65 0 0 0-1 1.51V21a2 2 0 0 1-4 0v-.09A1.65 1.65 0 0 0 9 19.4a1.65 1.65 0 0 0-1.82.33l-.06.06a2 2 0 0 1-2.83-2.83l.06-.06A1.65 1.65 0 0 0 4.68 15a1.65 1.65 0 0 0-1.51-1H3a2 2 0 0 1 0-4h.09A1.65 1.65 0 0 0 4.6 9a1.65 1.65 0 0 0-.33-1.82l-.06-.06a2 2 0 0 1 2.83-2.83l.06.06A1.65 1.65 0 0 0 9 4.68a1.65 1.65 0 0 0 1-1.51V3a2 2 0 0 1 4 0v.09a1.65 1.65 0 0 0 1 1.51 1.65 1.65 0 0 0 1.82-.33l.06-.06a2 2 0 0 1 2.83 2.83l-.06.06A1.65 1.65 0 0 0 19.4 9a1.65 1.65 0 0 0 1.51 1H21a2 2 0 0 1 0 4h-.09a1.65 1.65 0 0 0-1.51 1z"/></svg>`,
    iconBg: 'rgba(244, 114, 182, 0.10)',
    borderColor: 'rgba(244, 114, 182, 0.22)',
  },
]

const accessTiers = [
  {
    label: 'Young children',
    desc: 'A parent has full visibility into a young child\'s companion. They can review conversations, adjust data access, and configure what the model is exposed to.',
    color: 'linear-gradient(90deg, var(--purple), var(--violet))',
    labelColor: 'var(--purple-light)',
  },
  {
    label: 'Teenagers',
    desc: 'As a child grows, parental access gradually narrows. Teenagers gain increasing privacy over their companion, with parents retaining only a limited oversight role that fades over time.',
    color: 'linear-gradient(90deg, var(--violet), var(--pink))',
    labelColor: '#c084fc',
  },
  {
    label: 'Adults',
    desc: 'An adult\'s companion is theirs alone. No parent, no partner, no other family member has any access. The cryptographic link is exclusive and cannot be overridden by anyone.',
    color: 'linear-gradient(90deg, var(--pink), #f472b6)',
    labelColor: 'var(--pink-light)',
  },
]
</script>

<style scoped>
.cloud-section {
  padding: clamp(5rem, 10vw, 8rem) 0;
  position: relative;
}

.cloud-section::before {
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
  max-width: 600px;
}

.section-header.centered .section-sub {
  margin: 0 auto;
}

/* Cloud services grid */
.cloud-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 1.25rem;
  margin-bottom: 2rem;
}

.cloud-card {
  padding: 1.75rem;
}

.cloud-icon {
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

.cloud-title {
  font-size: 0.97rem;
  font-weight: 700;
  color: var(--text);
  margin-bottom: 0.6rem;
  letter-spacing: -0.01em;
}

.cloud-desc {
  font-size: 0.85rem;
  color: var(--text-secondary);
  line-height: 1.7;
}

/* Cryptographic identity */
.identity-callout {
  background: linear-gradient(135deg, rgba(99, 102, 241, 0.08) 0%, rgba(139, 92, 246, 0.05) 100%);
  border: 1px solid rgba(99, 102, 241, 0.22);
  border-radius: var(--radius-lg);
  padding: 2.5rem;
  margin-bottom: 2rem;
}

.identity-inner {
  display: flex;
  align-items: flex-start;
  gap: 1.75rem;
}

.identity-icon {
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

.identity-copy h3 {
  font-size: 1.15rem;
  font-weight: 800;
  letter-spacing: -0.02em;
  color: var(--text);
  margin-bottom: 0.75rem;
}

.identity-copy p {
  font-size: 0.95rem;
  color: var(--text-secondary);
  line-height: 1.75;
  max-width: 72ch;
}

/* Family access model */
.family-access {
  background: var(--bg-card);
  border: 1px solid var(--border);
  border-radius: var(--radius-lg);
  padding: 2.5rem;
  margin-bottom: 2rem;
}

.family-access-label {
  font-size: 0.7rem;
  font-weight: 700;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--purple-light);
  margin-bottom: 0.75rem;
}

.family-access-title {
  font-size: 1.15rem;
  font-weight: 800;
  letter-spacing: -0.02em;
  color: var(--text);
  margin-bottom: 0.6rem;
}

.family-access-sub {
  font-size: 0.9rem;
  color: var(--text-secondary);
  line-height: 1.7;
  max-width: 64ch;
  margin-bottom: 2rem;
}

.access-tiers {
  display: flex;
  flex-direction: column;
  gap: 1.25rem;
}

.access-tier {
  display: flex;
  align-items: flex-start;
  gap: 1.25rem;
}

.tier-bar {
  width: 4px;
  min-height: 100%;
  border-radius: 999px;
  flex-shrink: 0;
  align-self: stretch;
}

.tier-label {
  font-size: 0.82rem;
  font-weight: 700;
  letter-spacing: 0.04em;
  text-transform: uppercase;
  margin-bottom: 0.35rem;
}

.tier-desc {
  font-size: 0.88rem;
  color: var(--text-secondary);
  line-height: 1.7;
}

/* Portability callout */
.portability-callout {
  background: linear-gradient(135deg, rgba(236, 72, 153, 0.07) 0%, rgba(139, 92, 246, 0.05) 100%);
  border: 1px solid rgba(236, 72, 153, 0.2);
  border-radius: var(--radius-lg);
  padding: 2.5rem;
}

.portability-inner {
  display: flex;
  align-items: flex-start;
  gap: 1.75rem;
}

.portability-icon {
  width: 54px;
  height: 54px;
  display: flex;
  align-items: center;
  justify-content: center;
  background: rgba(236, 72, 153, 0.1);
  border: 1px solid rgba(236, 72, 153, 0.22);
  border-radius: 14px;
  color: var(--pink-light);
  flex-shrink: 0;
}

.portability-copy h3 {
  font-size: 1.15rem;
  font-weight: 800;
  letter-spacing: -0.02em;
  color: var(--text);
  margin-bottom: 0.75rem;
}

.portability-copy p {
  font-size: 0.95rem;
  color: var(--text-secondary);
  line-height: 1.75;
  max-width: 72ch;
}

@media (max-width: 768px) {
  .cloud-grid {
    grid-template-columns: 1fr;
  }
  .identity-inner,
  .portability-inner {
    flex-direction: column;
    gap: 1.25rem;
  }
}
</style>
