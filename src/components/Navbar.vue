<template>
  <nav class="navbar">
    <div class="nav-inner">
      <router-link to="/" class="logo">MKA</router-link>
      <div class="nav-links">
        <router-link to="/" class="nav-link" exact>Home</router-link>
        <router-link to="/about" class="nav-link">About</router-link>
        <router-link to="/skills" class="nav-link">Skills</router-link>
        <router-link to="/projects" class="nav-link">Projects</router-link>
        <router-link to="/contact" class="nav-link nav-cta">Contact</router-link>
      </div>
      <button class="mobile-toggle" @click="menuOpen = !menuOpen">
        <span></span><span></span><span></span>
      </button>
    </div>
    <div v-if="menuOpen" class="mobile-menu">
      <router-link to="/" class="mobile-link" @click="menuOpen = false">Home</router-link>
      <router-link to="/about" class="mobile-link" @click="menuOpen = false">About</router-link>
      <router-link to="/skills" class="mobile-link" @click="menuOpen = false">Skills</router-link>
      <router-link to="/projects" class="mobile-link" @click="menuOpen = false">Projects</router-link>
      <router-link to="/contact" class="mobile-link" @click="menuOpen = false">Contact</router-link>
    </div>
  </nav>
</template>

<script setup>
import { ref } from 'vue'
const menuOpen = ref(false)
</script>

<style scoped>
.navbar {
  position: fixed; top: 0; left: 0; right: 0;
  z-index: 1000;
  background: rgba(10,10,15,0.9);
  backdrop-filter: blur(20px);
  border-bottom: 1px solid var(--glass-border);
}

.nav-inner {
  max-width: 1200px; margin: 0 auto;
  padding: 15px 20px;
  display: flex; justify-content: space-between;
  align-items: center;
}

.logo {
  font-family: 'Orbitron', monospace;
  font-size: 28px; font-weight: 900;
  background: linear-gradient(135deg, var(--primary), var(--secondary));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.nav-links { display: flex; gap: 30px; align-items: center; }
@media (max-width: 768px) { .nav-links { display: none; } }

.nav-link {
  color: var(--text-muted);
  font-weight: 600; transition: color 0.3s;
  text-transform: uppercase; letter-spacing: 1px;
  font-size: 14px;
}

.nav-link:hover, .router-link-exact-active { color: var(--primary); }

.nav-cta {
  padding: 10px 25px;
  background: linear-gradient(135deg, var(--primary), var(--accent));
  border-radius: 50px; color: #fff !important;
}

.mobile-toggle {
  display: none;
  flex-direction: column; gap: 5px;
  background: none; border: none; cursor: pointer;
}
@media (max-width: 768px) { .mobile-toggle { display: flex; } }

.mobile-toggle span {
  width: 24px; height: 2px;
  background: #fff; transition: all 0.3s;
}

.mobile-menu {
  display: flex; flex-direction: column;
  padding: 20px; gap: 15px;
  background: rgba(10,10,15,0.95);
}

.mobile-link {
  color: var(--text-muted);
  font-weight: 600; font-size: 16px;
  padding: 10px; text-transform: uppercase;
  letter-spacing: 1px;
}
</style>

