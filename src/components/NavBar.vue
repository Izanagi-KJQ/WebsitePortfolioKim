<template>
  <header class="navbar" :class="{ scrolled: isScrolled }">
    <nav class="navbar__inner container">
      <!-- Logo -->
      <a href="#home" class="navbar__logo" @click.prevent="scrollTo('home')">
        <span class="logo-mark">KJ</span>
        <span class="logo-name">Kim John</span>
      </a>

      <!-- Nav Links (Desktop) -->
      <ul class="navbar__links">
        <li v-for="link in navLinks" :key="link.id">
          <a
            :href="`#${link.id}`"
            class="nav-link"
            :class="{ active: activeSection === link.id }"
            @click.prevent="scrollTo(link.id)"
          >{{ link.label }}</a>
        </li>
      </ul>

      <!-- CTA -->
      <div class="navbar__actions">
        <a href="mailto:kimjohn@email.com" class="btn-primary" style="text-decoration:none;display:inline-block">
          Let's Talk ✦
        </a>
        <!-- Hamburger -->
        <button class="hamburger" @click="mobileOpen = !mobileOpen" :class="{ open: mobileOpen }">
          <span></span><span></span><span></span>
        </button>
      </div>
    </nav>

    <!-- Mobile Menu -->
    <div class="mobile-menu" :class="{ open: mobileOpen }">
      <ul>
        <li v-for="link in navLinks" :key="link.id">
          <a :href="`#${link.id}`" @click.prevent="mobileNav(link.id)">{{ link.label }}</a>
        </li>
      </ul>
      <a href="mailto:kimjohn@email.com" class="btn-primary" style="text-decoration:none;display:inline-block;margin-top:1rem">
        Let's Talk ✦
      </a>
    </div>
  </header>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const isScrolled = ref(false)
const activeSection = ref('home')
const mobileOpen = ref(false)

const navLinks = [
  { id: 'home',         label: 'Home' },
  { id: 'works',        label: 'Works' },
  { id: 'about',        label: 'About' },
  { id: 'process',      label: 'Process' },
  { id: 'testimonials', label: 'Testimonials' },
  { id: 'contact',      label: 'Contact' },
]

const scrollTo = (id) => {
  const el = document.getElementById(id)
  if (el) el.scrollIntoView({ behavior: 'smooth' })
}

const mobileNav = (id) => {
  mobileOpen.value = false
  scrollTo(id)
}

const handleScroll = () => {
  isScrolled.value = window.scrollY > 20

  // Detect active section
  const sections = navLinks.map(l => l.id)
  for (let i = sections.length - 1; i >= 0; i--) {
    const el = document.getElementById(sections[i])
    if (el && window.scrollY >= el.offsetTop - 120) {
      activeSection.value = sections[i]
      break
    }
  }
}

onMounted(() => window.addEventListener('scroll', handleScroll, { passive: true }))
onUnmounted(() => window.removeEventListener('scroll', handleScroll))
</script>

<style scoped>
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 100;
  padding: 1.25rem 0;
  transition: all 0.4s cubic-bezier(0.16, 1, 0.3, 1);
}

.navbar.scrolled {
  padding: 0.85rem 0;
  backdrop-filter: blur(20px);
  -webkit-backdrop-filter: blur(20px);
  background: rgba(9, 10, 15, 0.85);
  border-bottom: 1px solid rgba(255,255,255,0.06);
}

.navbar__inner {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 2rem;
}

/* Logo */
.navbar__logo {
  display: flex;
  align-items: center;
  gap: 10px;
  text-decoration: none;
  flex-shrink: 0;
}

.logo-mark {
  width: 36px;
  height: 36px;
  border-radius: 10px;
  background: linear-gradient(135deg, #7928CA, #00DFD8);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 0.8rem;
  font-weight: 800;
  color: #fff;
  letter-spacing: -0.03em;
}

.logo-name {
  font-size: 0.95rem;
  font-weight: 700;
  color: #fff;
}

/* Nav Links */
.navbar__links {
  display: flex;
  list-style: none;
  gap: 0.25rem;
}

.nav-link {
  font-size: 0.875rem;
  font-weight: 500;
  color: rgba(255,255,255,0.55);
  padding: 0.4rem 0.9rem;
  border-radius: 999px;
  position: relative;
  transition: color 0.2s, background 0.2s;
}

.nav-link:hover,
.nav-link.active {
  color: #fff;
  background: rgba(255,255,255,0.07);
}

.nav-link.active::after {
  content: '';
  position: absolute;
  bottom: 2px;
  left: 50%;
  transform: translateX(-50%);
  width: 4px;
  height: 4px;
  background: #00DFD8;
  border-radius: 50%;
}

/* Actions */
.navbar__actions {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  flex-shrink: 0;
}

/* Hamburger */
.hamburger {
  display: none;
  flex-direction: column;
  gap: 5px;
  width: 28px;
  padding: 4px;
  cursor: pointer;
  background: none;
  border: none;
}

.hamburger span {
  display: block;
  height: 2px;
  background: rgba(255,255,255,0.7);
  border-radius: 2px;
  transition: all 0.3s;
}

.hamburger.open span:nth-child(1) { transform: translateY(7px) rotate(45deg); }
.hamburger.open span:nth-child(2) { opacity: 0; }
.hamburger.open span:nth-child(3) { transform: translateY(-7px) rotate(-45deg); }

/* Mobile Menu */
.mobile-menu {
  display: none;
  flex-direction: column;
  padding: 1.5rem 2rem;
  border-top: 1px solid rgba(255,255,255,0.06);
  background: rgba(9, 10, 15, 0.97);
  backdrop-filter: blur(20px);
  max-height: 0;
  overflow: hidden;
  transition: max-height 0.4s var(--ease-out), padding 0.3s;
}

.mobile-menu.open {
  max-height: 400px;
  padding: 1.5rem 2rem;
}

.mobile-menu ul { list-style: none; }
.mobile-menu ul li a {
  display: block;
  padding: 0.75rem 0;
  color: rgba(255,255,255,0.65);
  font-size: 1.05rem;
  font-weight: 500;
  border-bottom: 1px solid rgba(255,255,255,0.05);
  transition: color 0.2s;
}
.mobile-menu ul li a:hover { color: #fff; }

@media (max-width: 900px) {
  .navbar__links { display: none; }
  .hamburger { display: flex; }
  .mobile-menu { display: flex; }
}

@media (max-width: 500px) {
  .logo-name { display: none; }
}
</style>
