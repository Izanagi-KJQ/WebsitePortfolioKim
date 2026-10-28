<template>
  <section id="about" class="section">
    <div class="container">

      <div class="about-grid">
        <!-- Left: Bio -->
        <div class="about-bio">
          <div class="section-label">About Me</div>
          <h2 class="about-title">
            Designing with <span class="text-gradient">Purpose</span> &amp; Passion
          </h2>
          <p class="about-text">
            Hi! I'm <strong>Kim John Quiñonez</strong>, a UI/UX Designer &amp; Front-End Developer
            from the Philippines with 5+ years of experience creating intuitive digital products.
            I bridge the gap between beautiful design and clean, functional code.
          </p>
          <p class="about-text">
            My approach combines rigorous UX research with a deep appreciation for visual craft.
            Every pixel has a reason. Every interaction tells a story.
          </p>

          <div class="about-links">
            <a href="https://www.linkedin.com/in/kim-john-quiñonez-b3820b3b2" target="_blank" class="btn-primary" style="text-decoration:none;display:inline-block">
              LinkedIn Profile ↗
            </a>
            <a href="#contact" class="btn-ghost" @click.prevent="scrollTo('contact')">Download CV</a>
          </div>
        </div>

        <!-- Right: Skills -->
        <div class="about-skills">
          <!-- Tools -->
          <div class="skills-group glass-card">
            <h3 class="skills-group__title">
              <span class="skills-icon">🎨</span> Design Tools
            </h3>
            <div class="skills-pills">
              <span class="skill-badge" v-for="s in designSkills" :key="s">{{ s }}</span>
            </div>
          </div>

          <div class="skills-group glass-card">
            <h3 class="skills-group__title">
              <span class="skills-icon">⚡</span> Development
            </h3>
            <div class="skills-pills">
              <span class="skill-badge" v-for="s in devSkills" :key="s">{{ s }}</span>
            </div>
          </div>

          <!-- Mini stat cards -->
          <div class="mini-stats">
            <div class="mini-stat glass-card" v-for="s in miniStats" :key="s.label">
              <span class="mini-stat__num text-gradient">{{ s.num }}</span>
              <span class="mini-stat__label">{{ s.label }}</span>
            </div>
          </div>
        </div>
      </div>

    </div>
  </section>
</template>

<script setup>
const designSkills = ['Figma', 'Adobe XD', 'Illustrator', 'Photoshop', 'Framer', 'Principle']
const devSkills = ['Vue.js', 'React', 'Laravel', 'Vite', 'HTML/CSS', 'JavaScript', 'Tailwind']
const miniStats = [
  { num: '50+', label: 'Projects Completed' },
  { num: '30+', label: 'Happy Clients' },
  { num: '5+',  label: 'Years Experience' },
  { num: '100%', label: 'Client Satisfaction' },
]
const scrollTo = (id) => {
  const el = document.getElementById(id)
  if (el) el.scrollIntoView({ behavior: 'smooth' })
}
</script>

<style scoped>
.about-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 5rem;
  align-items: flex-start;
}

.about-title {
  font-size: clamp(1.8rem, 3.5vw, 2.75rem);
  font-weight: 800;
  letter-spacing: -0.03em;
  line-height: 1.15;
  margin-bottom: 1.25rem;
  margin-top: 0.5rem;
}

.about-text {
  color: rgba(255,255,255,0.55);
  font-size: 1rem;
  line-height: 1.75;
  margin-bottom: 1rem;
}

.about-links {
  display: flex;
  gap: 1rem;
  flex-wrap: wrap;
  margin-top: 2rem;
}

/* Skills */
.about-skills {
  display: flex;
  flex-direction: column;
  gap: 1.25rem;
}

.skills-group {
  padding: 1.5rem;
}

.skills-group__title {
  font-size: 0.875rem;
  font-weight: 700;
  color: rgba(255,255,255,0.6);
  text-transform: uppercase;
  letter-spacing: 0.08em;
  margin-bottom: 1rem;
  display: flex;
  align-items: center;
  gap: 8px;
}

.skills-icon { font-size: 1rem; }

.skills-pills {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
}

.skill-badge {
  background: linear-gradient(135deg, rgba(121,40,202,0.2), rgba(0,223,216,0.1));
  border: 1px solid rgba(121,40,202,0.3);
  color: rgba(255,255,255,0.8);
  padding: 5px 14px;
  border-radius: 999px;
  font-size: 0.8rem;
  font-weight: 600;
  transition: border-color 0.2s, background 0.2s;
}

.skill-badge:hover {
  border-color: rgba(0, 223, 216, 0.5);
  background: rgba(0, 223, 216, 0.12);
}

/* Mini stats */
.mini-stats {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1rem;
}

.mini-stat {
  padding: 1.25rem;
  text-align: center;
  display: flex;
  flex-direction: column;
  gap: 4px;
}

.mini-stat__num {
  font-size: 1.75rem;
  font-weight: 800;
  letter-spacing: -0.04em;
  line-height: 1;
}

.mini-stat__label {
  font-size: 0.72rem;
  color: rgba(255,255,255,0.4);
  font-weight: 500;
  text-transform: uppercase;
  letter-spacing: 0.06em;
}

@media (max-width: 900px) {
  .about-grid { grid-template-columns: 1fr; gap: 3rem; }
}

@media (max-width: 500px) {
  .mini-stats { grid-template-columns: 1fr 1fr; }
}
</style>
