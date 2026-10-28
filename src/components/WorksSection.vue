<template>
  <section id="works" class="section">
    <div class="container">
      <div class="section-header">
        <div class="section-label">My Portfolio</div>
        <h2 class="section-title">Selected <span class="text-gradient">Works</span></h2>
        <p class="section-desc">A curated selection of projects that reflect my craft, curiosity, and commitment to purposeful design.</p>
      </div>

      <!-- Bento Grid -->
      <div class="bento-grid">
        <!-- Large card -->
        <div
          v-for="(project, i) in projects"
          :key="i"
          class="project-card glass-card"
          :class="project.size"
          @mouseenter="hoveredCard = i"
          @mouseleave="hoveredCard = null"
        >
          <div class="card-image">
            <img :src="project.image" :alt="project.title" />
            <div class="card-overlay">
              <a :href="project.url" class="card-visit">View Project ↗</a>
            </div>
          </div>
          <div class="card-body">
            <div class="card-meta">
              <span class="card-year">{{ project.year }}</span>
              <div class="card-tags">
                <span class="tag-pill" v-for="tag in project.tags" :key="tag">{{ tag }}</span>
              </div>
            </div>
            <h3 class="card-title">{{ project.title }}</h3>
            <p class="card-desc">{{ project.desc }}</p>
          </div>
        </div>
      </div>

      <!-- Bottom CTA -->
      <div class="works-cta">
        <p class="works-cta__text">Want to see more?</p>
        <a href="https://github.com/Izanagi-KJQ" target="_blank" class="btn-ghost">
          View All on GitHub ↗
        </a>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'
import proj1 from '../assets/project1.png'
import proj2 from '../assets/project2.png'
import proj3 from '../assets/project3.png'

const hoveredCard = ref(null)

const projects = [
  {
    title: 'FinTrack — Fintech Dashboard',
    desc: 'A mobile-first personal finance app with real-time expense tracking, AI-powered insights, and beautiful data visualizations.',
    image: proj1,
    tags: ['UI/UX', 'Mobile', 'Figma', 'Vue'],
    year: '2024',
    size: 'card--lg',
    url: '#',
  },
  {
    title: 'ShopVault — E-Commerce Platform',
    desc: 'A sleek e-commerce web experience with advanced product filtering, glassmorphism UI components, and seamless checkout flow.',
    image: proj2,
    tags: ['Web Design', 'UX Research', 'Laravel'],
    year: '2024',
    size: 'card--md',
    url: '#',
  },
  {
    title: 'FitFlow — Fitness Tracker App',
    desc: 'A health and wellness app featuring personalized workout plans, progress rings, and a motivating streak system.',
    image: proj3,
    tags: ['Mobile', 'UI Design', 'React Native'],
    year: '2023',
    size: 'card--md',
    url: '#',
  },
]
</script>

<style scoped>
.section-header {
  text-align: center;
  margin-bottom: 4rem;
}

.section-title {
  font-size: clamp(2rem, 4vw, 3rem);
  font-weight: 800;
  letter-spacing: -0.03em;
  margin-bottom: 1rem;
}

.section-desc {
  color: rgba(255,255,255,0.5);
  max-width: 480px;
  margin: 0 auto;
  font-size: 1rem;
  line-height: 1.7;
}

/* Bento Grid */
.bento-grid {
  display: grid;
  grid-template-columns: repeat(12, 1fr);
  gap: 1.25rem;
}

.project-card {
  overflow: hidden;
  cursor: pointer;
  transition: transform 0.35s cubic-bezier(0.16, 1, 0.3, 1), box-shadow 0.35s;
}

.project-card:hover {
  transform: translateY(-4px);
}

.card--lg { grid-column: span 12; }
.card--md { grid-column: span 6; }

/* Card Image */
.card-image {
  position: relative;
  overflow: hidden;
  aspect-ratio: 16/7;
}

.card--md .card-image { aspect-ratio: 4/3; }

.card-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.5s cubic-bezier(0.16, 1, 0.3, 1);
}

.project-card:hover .card-image img {
  transform: scale(1.06);
}

.card-overlay {
  position: absolute;
  inset: 0;
  background: rgba(9, 10, 15, 0.6);
  backdrop-filter: blur(4px);
  display: flex;
  align-items: center;
  justify-content: center;
  opacity: 0;
  transition: opacity 0.3s;
}

.project-card:hover .card-overlay { opacity: 1; }

.card-visit {
  background: linear-gradient(135deg, #7928CA, #00DFD8);
  color: #fff;
  font-weight: 700;
  font-size: 0.9rem;
  padding: 0.75rem 2rem;
  border-radius: 999px;
  text-decoration: none;
  transition: transform 0.2s;
}
.card-visit:hover { transform: scale(1.05); }

/* Card Body */
.card-body {
  padding: 1.5rem;
}

.card-meta {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 1rem;
  flex-wrap: wrap;
  margin-bottom: 0.85rem;
}

.card-year {
  font-size: 0.75rem;
  color: rgba(255,255,255,0.3);
  font-weight: 600;
  letter-spacing: 0.08em;
}

.card-tags {
  display: flex;
  gap: 6px;
  flex-wrap: wrap;
}

.card-title {
  font-size: 1.25rem;
  font-weight: 700;
  letter-spacing: -0.02em;
  margin-bottom: 0.5rem;
}

.card-desc {
  font-size: 0.875rem;
  color: rgba(255,255,255,0.45);
  line-height: 1.6;
}

/* CTA */
.works-cta {
  margin-top: 3.5rem;
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 1.25rem;
  flex-wrap: wrap;
}

.works-cta__text {
  color: rgba(255,255,255,0.4);
  font-size: 0.9rem;
}

/* Responsive */
@media (max-width: 768px) {
  .card--lg, .card--md { grid-column: span 12; }
}
</style>
