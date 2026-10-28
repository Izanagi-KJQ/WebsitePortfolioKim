<template>
  <section id="testimonials" class="section">
    <div class="container">
      <div class="section-header">
        <div class="section-label">Social Proof</div>
        <h2 class="section-title">What Clients <span class="text-gradient">Say</span></h2>
      </div>

      <div class="testimonials-grid">
        <div
          class="testimonial-card glass-card"
          v-for="(t, i) in testimonials"
          :key="i"
          :class="{ 'featured': t.featured }"
        >
          <div class="quote-icon">"</div>
          <p class="testimonial-text">{{ t.text }}</p>
          <div class="testimonial-author">
            <div class="author-avatar">{{ t.initials }}</div>
            <div class="author-info">
              <div class="author-name">{{ t.name }}</div>
              <div class="author-role">{{ t.role }}</div>
            </div>
            <div class="author-stars">
              <span v-for="s in 5" :key="s">★</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const testimonials = [
  {
    text: "Kim John doesn't just design interfaces — he crafts experiences. His ability to align user needs with business goals resulted in a 40% increase in our app's retention rate.",
    name: "Sarah Chen",
    role: "Product Manager @ TechVault",
    initials: "SC",
    featured: true,
  },
  {
    text: "An exceptional designer with incredible attention to detail. The design system Kim built has saved our team countless hours and maintains perfect consistency.",
    name: "Marcus Rivera",
    role: "Engineering Lead @ FinTrack",
    initials: "MR",
    featured: false,
  },
  {
    text: "Working with Kim was a game-changer for our brand. He transformed our outdated platform into a modern, beautiful product our users actually love.",
    name: "Aisha Wongso",
    role: "CEO @ ShopVault",
    initials: "AW",
    featured: false,
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
}

/* Grid */
.testimonials-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1.25rem;
}

.testimonial-card {
  padding: 2rem;
  position: relative;
  display: flex;
  flex-direction: column;
  gap: 1.25rem;
  transition: transform 0.35s cubic-bezier(0.16, 1, 0.3, 1);
}

.testimonial-card:hover {
  transform: translateY(-4px);
}

.testimonial-card.featured {
  background: linear-gradient(135deg, rgba(121, 40, 202, 0.15), rgba(0, 223, 216, 0.06));
  border-color: rgba(121, 40, 202, 0.35);
}

.quote-icon {
  font-size: 4rem;
  line-height: 1;
  background: var(--grad-primary);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  font-family: Georgia, serif;
  margin-top: -0.5rem;
}

.testimonial-text {
  font-size: 0.95rem;
  color: rgba(255,255,255,0.65);
  line-height: 1.75;
  flex: 1;
}

/* Author */
.testimonial-author {
  display: flex;
  align-items: center;
  gap: 12px;
  border-top: 1px solid rgba(255,255,255,0.06);
  padding-top: 1.25rem;
}

.author-avatar {
  width: 42px;
  height: 42px;
  border-radius: 50%;
  background: var(--grad-primary);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 0.8rem;
  font-weight: 800;
  color: #fff;
  flex-shrink: 0;
}

.author-name {
  font-size: 0.875rem;
  font-weight: 700;
  color: #fff;
}

.author-role {
  font-size: 0.75rem;
  color: rgba(255,255,255,0.4);
}

.author-stars {
  margin-left: auto;
  color: #FFD700;
  font-size: 0.8rem;
  letter-spacing: 1px;
  flex-shrink: 0;
}

@media (max-width: 900px) {
  .testimonials-grid { grid-template-columns: 1fr; }
}

@media (max-width: 700px) {
  .testimonials-grid { grid-template-columns: 1fr; }
}
</style>
