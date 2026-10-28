<template>
  <section id="home" class="hero">
    <!-- Ambient background glows -->
    <div class="hero__glow hero__glow--violet"></div>
    <div class="hero__glow hero__glow--cyan"></div>
    <div class="hero__glow hero__glow--pink"></div>

    <div class="container hero__inner">
      <!-- Left: Text content -->
      <div class="hero__content">
        <!-- Availability badge -->
        <div class="hero__badge">
          <span class="pulse-dot"></span>
          Available for new projects
        </div>

        <!-- Headline -->
        <h1 class="hero__headline">
          Crafting<br>
          <span class="text-gradient">Intuitive</span> Digital<br>
          Experiences
        </h1>

        <!-- Subheadline -->
        <p class="hero__sub">
          UI/UX Designer &amp; Front-End Developer based in the Philippines.
          I design and build elegant, user-centered products that people love.
        </p>

        <!-- Stats row -->
        <div class="hero__stats">
          <div class="stat" v-for="s in stats" :key="s.label">
            <span class="stat__num text-gradient">{{ s.num }}</span>
            <span class="stat__label">{{ s.label }}</span>
          </div>
        </div>

        <!-- CTAs -->
        <div class="hero__ctas">
          <a href="#works" class="btn-primary" @click.prevent="scrollTo('works')">View My Work ↓</a>
          <a href="#contact" class="btn-ghost" @click.prevent="scrollTo('contact')">Get in Touch</a>
        </div>
      </div>

      <!-- Right: Profile visual -->
      <div class="hero__visual">
        <div class="profile-frame">
          <div class="profile-frame__ring"></div>
          <img src="../assets/profile.png" alt="Kim John Quiñonez" class="profile-img" />

          <!-- Floating cards -->
          <div class="float-card float-card--tl">
            <span class="float-icon">🎨</span>
            <div>
              <div class="float-title">UI Design</div>
              <div class="float-sub">Figma Expert</div>
            </div>
          </div>

          <div class="float-card float-card--br">
            <span class="float-icon">⚡</span>
            <div>
              <div class="float-title">5+ Years</div>
              <div class="float-sub">Experience</div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Scroll indicator -->
    <div class="scroll-indicator">
      <div class="scroll-line"></div>
      <span>Scroll</span>
    </div>
  </section>
</template>

<script setup>
const stats = [
  { num: '50+', label: 'Projects' },
  { num: '30+', label: 'Clients' },
  { num: '5+',  label: 'Years Exp.' },
]

const scrollTo = (id) => {
  const el = document.getElementById(id)
  if (el) el.scrollIntoView({ behavior: 'smooth' })
}
</script>

<style scoped>
.hero {
  position: relative;
  min-height: 100vh;
  display: flex;
  align-items: center;
  padding-top: 5rem;
  overflow: hidden;
}

/* Glows */
.hero__glow {
  position: absolute;
  border-radius: 50%;
  filter: blur(100px);
  pointer-events: none;
  animation: float 8s ease-in-out infinite;
}

.hero__glow--violet {
  width: 600px;
  height: 600px;
  background: rgba(121, 40, 202, 0.2);
  top: -10%;
  left: -10%;
  animation-delay: 0s;
}

.hero__glow--cyan {
  width: 500px;
  height: 500px;
  background: rgba(0, 223, 216, 0.12);
  top: 20%;
  right: -5%;
  animation-delay: 3s;
}

.hero__glow--pink {
  width: 400px;
  height: 400px;
  background: rgba(255, 0, 127, 0.08);
  bottom: 0;
  left: 40%;
  animation-delay: 6s;
}

/* Layout */
.hero__inner {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 4rem;
  align-items: center;
  padding-top: 2rem;
  padding-bottom: 4rem;
}

/* Badge */
.hero__badge {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  background: rgba(16, 185, 129, 0.1);
  border: 1px solid rgba(16, 185, 129, 0.25);
  border-radius: 999px;
  padding: 6px 16px 6px 10px;
  font-size: 0.8rem;
  font-weight: 600;
  color: #34d399;
  margin-bottom: 1.5rem;
  animation: fadeInUp 0.6s ease both;
}

.pulse-dot {
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background: #10B981;
  animation: pulse-dot 2s ease-in-out infinite;
  flex-shrink: 0;
}

/* Headline */
.hero__headline {
  font-size: clamp(2.8rem, 5vw, 4.5rem);
  font-weight: 800;
  line-height: 1.08;
  letter-spacing: -0.03em;
  margin-bottom: 1.5rem;
  animation: fadeInUp 0.7s ease 0.1s both;
}

/* Subheadline */
.hero__sub {
  font-size: 1.05rem;
  color: rgba(255,255,255,0.55);
  max-width: 480px;
  line-height: 1.7;
  margin-bottom: 2rem;
  animation: fadeInUp 0.7s ease 0.2s both;
}

/* Stats */
.hero__stats {
  display: flex;
  gap: 2.5rem;
  margin-bottom: 2.5rem;
  animation: fadeInUp 0.7s ease 0.3s both;
}

.stat {
  display: flex;
  flex-direction: column;
  gap: 2px;
}

.stat__num {
  font-size: 2rem;
  font-weight: 800;
  letter-spacing: -0.04em;
  line-height: 1;
}

.stat__label {
  font-size: 0.78rem;
  color: rgba(255,255,255,0.4);
  font-weight: 500;
  text-transform: uppercase;
  letter-spacing: 0.06em;
}

/* CTAs */
.hero__ctas {
  display: flex;
  gap: 1rem;
  flex-wrap: wrap;
  animation: fadeInUp 0.7s ease 0.4s both;
}

/* Profile visual */
.hero__visual {
  display: flex;
  justify-content: center;
  align-items: center;
  position: relative;
  animation: fadeInUp 0.9s ease 0.2s both;
}

.profile-frame {
  position: relative;
  width: 380px;
  height: 440px;
}

.profile-frame__ring {
  position: absolute;
  inset: -16px;
  border-radius: 48px;
  background: var(--grad-primary);
  opacity: 0.2;
  animation: rotate-slow 15s linear infinite;
  z-index: 0;
}

.profile-img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  border-radius: 40px;
  position: relative;
  z-index: 1;
  border: 2px solid rgba(255,255,255,0.08);
}

/* Floating Cards */
.float-card {
  position: absolute;
  z-index: 2;
  background: rgba(255,255,255,0.07);
  border: 1px solid rgba(255,255,255,0.12);
  backdrop-filter: blur(16px);
  border-radius: 16px;
  padding: 10px 16px;
  display: flex;
  align-items: center;
  gap: 10px;
  min-width: 140px;
  animation: float 5s ease-in-out infinite;
}

.float-card--tl {
  top: 20px;
  left: -60px;
  animation-delay: 1s;
}

.float-card--br {
  bottom: 30px;
  right: -50px;
  animation-delay: 2.5s;
}

.float-icon {
  font-size: 1.4rem;
}

.float-title {
  font-size: 0.85rem;
  font-weight: 700;
  color: #fff;
}

.float-sub {
  font-size: 0.72rem;
  color: rgba(255,255,255,0.5);
}

/* Scroll indicator */
.scroll-indicator {
  position: absolute;
  bottom: 2.5rem;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 8px;
  color: rgba(255,255,255,0.3);
  font-size: 0.7rem;
  letter-spacing: 0.12em;
  text-transform: uppercase;
}

.scroll-line {
  width: 1px;
  height: 48px;
  background: linear-gradient(to bottom, rgba(121,40,202,0.6), transparent);
  animation: float 2s ease-in-out infinite;
}

/* Responsive */
@media (max-width: 900px) {
  .hero__inner {
    grid-template-columns: 1fr;
    gap: 3rem;
    text-align: center;
  }

  .hero__sub { max-width: 100%; }
  .hero__ctas { justify-content: center; }
  .hero__stats { justify-content: center; }

  .hero__visual { order: -1; }
  .profile-frame { width: 280px; height: 320px; }
  .float-card--tl { left: -20px; }
  .float-card--br { right: -20px; }
}

@media (max-width: 500px) {
  .profile-frame { width: 240px; height: 280px; }
  .float-card { display: none; }
}
</style>
