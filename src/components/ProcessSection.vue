<template>
  <section id="process" class="section process-section">
    <!-- Glow background -->
    <div class="process-glow"></div>

    <div class="container">
      <div class="section-header">
        <div class="section-label">My Approach</div>
        <h2 class="section-title">The Design <span class="text-gradient">Process</span></h2>
        <p class="section-desc">How I transform ideas into meaningful user experiences — systematically.</p>
      </div>

      <div class="process-grid">
        <div
          class="process-step glass-card"
          v-for="(step, i) in steps"
          :key="i"
          :class="{ 'active-step': activeStep === i }"
          @mouseenter="activeStep = i"
          @mouseleave="activeStep = null"
        >
          <div class="step-number">0{{ i + 1 }}</div>
          <div class="step-icon">{{ step.icon }}</div>
          <h3 class="step-title">{{ step.title }}</h3>
          <p class="step-desc">{{ step.desc }}</p>
          <div class="step-methods">
            <span class="tag-pill" v-for="m in step.methods" :key="m">{{ m }}</span>
          </div>
          <!-- Connector line -->
          <div class="step-connector" v-if="i < steps.length - 1"></div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'

const activeStep = ref(0)

const steps = [
  {
    icon: '🔍',
    title: 'Discover',
    desc: 'Deep-dive research to understand user needs, pain points, business goals, and competitive landscape.',
    methods: ['User Interviews', 'Surveys', 'Competitive Analysis'],
  },
  {
    icon: '🧠',
    title: 'Define',
    desc: 'Synthesize research findings into clear problem statements, user personas, and information architecture.',
    methods: ['Affinity Mapping', 'User Flows', 'Personas'],
  },
  {
    icon: '🎨',
    title: 'Design',
    desc: 'From low-fidelity wireframes to high-fidelity prototypes — iterating fast, validating faster.',
    methods: ['Wireframing', 'Prototyping', 'Design Systems'],
  },
  {
    icon: '🚀',
    title: 'Deliver',
    desc: 'Handoff with precision: annotated specs, dev-ready components, and post-launch performance tracking.',
    methods: ['Dev Handoff', 'QA Review', 'Usability Testing'],
  },
]
</script>

<style scoped>
.process-section {
  position: relative;
  overflow: hidden;
}

.process-glow {
  position: absolute;
  width: 700px;
  height: 700px;
  border-radius: 50%;
  background: rgba(0, 223, 216, 0.08);
  filter: blur(120px);
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  pointer-events: none;
}

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

/* Grid */
.process-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 1.25rem;
  position: relative;
}

/* Step card */
.process-step {
  padding: 2rem 1.5rem;
  position: relative;
  text-align: center;
  cursor: default;
  transition: transform 0.35s cubic-bezier(0.16, 1, 0.3, 1), box-shadow 0.35s;
}

.process-step.active-step,
.process-step:hover {
  transform: translateY(-6px);
  border-color: rgba(121, 40, 202, 0.5);
  box-shadow: 0 24px 60px rgba(121, 40, 202, 0.15);
}

.step-number {
  font-size: 3rem;
  font-weight: 900;
  letter-spacing: -0.06em;
  line-height: 1;
  color: rgba(255,255,255,0.05);
  margin-bottom: 1rem;
  font-variant-numeric: tabular-nums;
}

.active-step .step-number,
.process-step:hover .step-number {
  background: var(--grad-text);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  opacity: 1;
}

.step-icon {
  font-size: 2rem;
  margin-bottom: 1rem;
}

.step-title {
  font-size: 1.15rem;
  font-weight: 800;
  letter-spacing: -0.02em;
  margin-bottom: 0.75rem;
}

.step-desc {
  font-size: 0.85rem;
  color: rgba(255,255,255,0.45);
  line-height: 1.7;
  margin-bottom: 1.25rem;
}

.step-methods {
  display: flex;
  flex-wrap: wrap;
  gap: 6px;
  justify-content: center;
}

/* Connector */
.step-connector {
  position: absolute;
  top: 2.5rem;
  right: -0.625rem;
  width: 1.25rem;
  height: 1px;
  background: linear-gradient(to right, rgba(121,40,202,0.5), rgba(0,223,216,0.5));
  z-index: 2;
}

@media (max-width: 900px) {
  .process-grid { grid-template-columns: repeat(2, 1fr); }
  .step-connector { display: none; }
}

@media (max-width: 500px) {
  .process-grid { grid-template-columns: 1fr; }
}
</style>
