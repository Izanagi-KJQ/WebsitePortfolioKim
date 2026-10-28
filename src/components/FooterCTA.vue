<template>
  <footer id="contact" class="footer">
    <!-- Glow -->
    <div class="footer-glow footer-glow--violet"></div>
    <div class="footer-glow footer-glow--cyan"></div>

    <div class="container">
      <!-- CTA -->
      <div class="footer-cta">
        <div class="footer-tag section-label">Open For Work</div>
        <h2 class="footer-headline">
          Let's Build Something<br>
          <span class="text-gradient">Iconic</span> Together
        </h2>
        <p class="footer-sub">
          Have a project in mind? I'd love to hear about it. Let's create something remarkable.
        </p>

        <div class="footer-actions">
          <!-- Email copy -->
          <button class="email-btn" @click="copyEmail">
            <span class="email-text">{{ emailDisplay }}</span>
            <span class="copy-icon">{{ copied ? '✓' : '⎘' }}</span>
          </button>

          <a href="mailto:kimjohn@email.com" class="btn-primary" style="text-decoration:none;display:inline-block">
            Send Email ↗
          </a>
        </div>

        <!-- Copied toast -->
        <transition name="toast">
          <div class="toast" v-if="copied">Email copied to clipboard! ✨</div>
        </transition>
      </div>

      <hr class="divider footer-divider" />

      <!-- Bottom bar -->
      <div class="footer-bottom">
        <div class="footer-logo">
          <span class="logo-mark-sm">KJ</span>
          <span class="footer-name">Kim John Quiñonez</span>
        </div>

        <p class="footer-copy">
          © {{ year }} · Designed &amp; Built with ♥
        </p>

        <!-- Social links -->
        <div class="social-links">
          <a
            v-for="link in socials"
            :key="link.label"
            :href="link.url"
            target="_blank"
            class="social-link"
            :title="link.label"
          >
            <span v-html="link.icon"></span>
          </a>
        </div>
      </div>
    </div>
  </footer>
</template>

<script setup>
import { ref } from 'vue'

const year = new Date().getFullYear()
const emailDisplay = ref('kimjohn@email.com')
const copied = ref(false)

const copyEmail = () => {
  navigator.clipboard.writeText('kimjohn@email.com').then(() => {
    copied.value = true
    emailDisplay.value = 'Copied!'
    setTimeout(() => {
      copied.value = false
      emailDisplay.value = 'kimjohn@email.com'
    }, 2500)
  })
}

const socials = [
  {
    label: 'LinkedIn',
    url: 'https://www.linkedin.com/in/kim-john-qui%C3%B1onez-b3820b3b2',
    icon: `<svg width="18" height="18" viewBox="0 0 24 24" fill="currentColor"><path d="M16 8a6 6 0 0 1 6 6v7h-4v-7a2 2 0 0 0-2-2 2 2 0 0 0-2 2v7h-4v-7a6 6 0 0 1 6-6z"/><rect x="2" y="9" width="4" height="12"/><circle cx="4" cy="4" r="2"/></svg>`,
  },
  {
    label: 'GitHub',
    url: 'https://github.com/Izanagi-KJQ',
    icon: `<svg width="18" height="18" viewBox="0 0 24 24" fill="currentColor"><path d="M9 19c-5 1.5-5-2.5-7-3m14 6v-3.87a3.37 3.37 0 0 0-.94-2.61c3.14-.35 6.44-1.54 6.44-7A5.44 5.44 0 0 0 20 4.77 5.07 5.07 0 0 0 19.91 1S18.73.65 16 2.48a13.38 13.38 0 0 0-7 0C6.27.65 5.09 1 5.09 1A5.07 5.07 0 0 0 5 4.77a5.44 5.44 0 0 0-1.5 3.78c0 5.42 3.3 6.61 6.44 7A3.37 3.37 0 0 0 9 18.13V22"/></svg>`,
  },
  {
    label: 'Dribbble',
    url: 'https://dribbble.com',
    icon: `<svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><path d="M8.56 2.75c4.37 6.03 6.02 9.42 8.03 17.72m2.54-15.38c-3.72 4.35-8.94 5.66-16.88 5.85m19.5 1.9c-3.5-.93-6.63-.82-8.94 0-2.58.92-5.01 2.86-7.44 6.32"/></svg>`,
  },
]
</script>

<style scoped>
.footer {
  position: relative;
  padding: 6rem 0 3rem;
  overflow: hidden;
  border-top: 1px solid rgba(255,255,255,0.05);
}

/* Glows */
.footer-glow {
  position: absolute;
  border-radius: 50%;
  filter: blur(120px);
  pointer-events: none;
}
.footer-glow--violet {
  width: 500px; height: 500px;
  background: rgba(121, 40, 202, 0.15);
  bottom: -15%;
  left: -10%;
}
.footer-glow--cyan {
  width: 400px; height: 400px;
  background: rgba(0, 223, 216, 0.1);
  top: 0;
  right: -5%;
}

/* CTA */
.footer-cta {
  text-align: center;
  position: relative;
  z-index: 1;
}

.footer-tag { margin-bottom: 1.25rem; }

.footer-headline {
  font-size: clamp(2.4rem, 5vw, 4.5rem);
  font-weight: 900;
  letter-spacing: -0.04em;
  line-height: 1.1;
  margin-bottom: 1.25rem;
}

.footer-sub {
  color: rgba(255,255,255,0.5);
  font-size: 1.05rem;
  margin-bottom: 2.5rem;
  line-height: 1.7;
}

.footer-actions {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 1rem;
  flex-wrap: wrap;
}

/* Email copy button */
.email-btn {
  display: inline-flex;
  align-items: center;
  gap: 10px;
  background: rgba(255,255,255,0.05);
  border: 1px solid rgba(255,255,255,0.1);
  color: rgba(255,255,255,0.8);
  padding: 0.65rem 1.5rem;
  border-radius: 999px;
  font-family: var(--font);
  font-size: 0.875rem;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.2s;
}

.email-btn:hover {
  background: rgba(255,255,255,0.09);
  border-color: rgba(121, 40, 202, 0.4);
  color: #fff;
}

.copy-icon {
  font-size: 1rem;
  opacity: 0.6;
}

/* Toast */
.toast {
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
  margin-top: 1rem;
  background: rgba(16, 185, 129, 0.15);
  border: 1px solid rgba(16, 185, 129, 0.4);
  color: #34d399;
  padding: 8px 20px;
  border-radius: 999px;
  font-size: 0.8rem;
  font-weight: 600;
  white-space: nowrap;
}

.toast-enter-active, .toast-leave-active { transition: all 0.3s ease; }
.toast-enter-from, .toast-leave-to { opacity: 0; transform: translateX(-50%) translateY(8px); }

/* Divider */
.footer-divider { margin: 4rem 0 2rem; }

/* Bottom bar */
.footer-bottom {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 1.5rem;
  flex-wrap: wrap;
}

.footer-logo {
  display: flex;
  align-items: center;
  gap: 10px;
}

.logo-mark-sm {
  width: 32px;
  height: 32px;
  border-radius: 8px;
  background: linear-gradient(135deg, #7928CA, #00DFD8);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 0.7rem;
  font-weight: 800;
  color: #fff;
}

.footer-name {
  font-size: 0.85rem;
  font-weight: 600;
  color: rgba(255,255,255,0.7);
}

.footer-copy {
  color: rgba(255,255,255,0.3);
  font-size: 0.8rem;
}

/* Social links */
.social-links {
  display: flex;
  gap: 0.5rem;
}

.social-link {
  width: 38px;
  height: 38px;
  border-radius: 10px;
  background: rgba(255,255,255,0.05);
  border: 1px solid rgba(255,255,255,0.08);
  display: flex;
  align-items: center;
  justify-content: center;
  color: rgba(255,255,255,0.5);
  transition: all 0.2s;
  text-decoration: none;
}

.social-link:hover {
  background: rgba(121, 40, 202, 0.15);
  border-color: rgba(121, 40, 202, 0.4);
  color: #a78bfa;
  transform: translateY(-2px);
}

@media (max-width: 600px) {
  .footer-bottom { justify-content: center; text-align: center; flex-direction: column; }
}
</style>
