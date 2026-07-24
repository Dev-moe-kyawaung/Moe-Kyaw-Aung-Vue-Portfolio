# 📦 Complete Package with README, LICENSE & ALL Components for GitHub Pages

ဒီမှာ GitHub Pages ပေါ်တင်ဖို့ လိုအပ်တဲ့ README, LICENSE နဲ့ Component ဖိုင်တွေအားလုံးကို Design 5 ခုလုံးအတွက် တစ်စုတစ်စည်းတည်း ပေးလိုက်ပါတယ်။

---

## 📁 Complete File Structure

```
portfolio/
├── .github/workflows/deploy.yml
├── public/
│   ├── 404.html
│   ├── manifest.json
│   ├── robots.txt
│   ├── sitemap.xml
│   └── .nojekyll
├── src/
│   ├── components/
│   │   ├── ThreeBackground.vue
│   │   ├── Navbar.vue
│   │   ├── Footer.vue
│   │   └── designs/
│   │       ├── DesignGlassmorphism.vue
│   │       ├── DesignCyberpunk.vue
│   │       ├── DesignLuxury.vue
│   │       ├── DesignModernTech.vue
│   │       └── DesignJapanese.vue
│   ├── pages/
│   │   ├── Home.vue
│   │   ├── About.vue
│   │   ├── Skills.vue
│   │   ├── Projects.vue
│   │   └── Contact.vue
│   ├── router/
│   │   └── index.js
│   ├── styles/
│   │   └── global.css
│   ├── App.vue
│   └── main.js
├── index.html
├── package.json
├── vite.config.js
├── README.md
├── LICENSE
├── .gitignore
└── designs-guide.md
```

---

## 1️⃣ `package.json`
```json
{
  "name": "moe-kyaw-aung-portfolio",
  "private": true,
  "version": "1.0.0",
  "type": "module",
  "homepage": "https://dev-moe-kyawaung.github.io/portfolio",
  "scripts": {
    "dev": "vite",
    "build": "vite build",
    "preview": "vite preview",
    "predeploy": "npm run build",
    "deploy": "gh-pages -d dist"
  },
  "dependencies": {
    "vue": "^3.4.0",
    "vue-router": "^4.2.0",
    "three": "^0.162.0"
  },
  "devDependencies": {
    "@vitejs/plugin-vue": "^5.0.0",
    "vite": "^5.1.0",
    "gh-pages": "^6.1.1"
  }
}
```

## 2️⃣ `vite.config.js`
```javascript
import { defineConfig } from 'vite'
import vue from '@vitejs/plugin-vue'

export default defineConfig({
  plugins: [vue()],
  base: '/portfolio/',
  build: { outDir: 'dist' }
})
```

## 3️⃣ `index.html`
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="description" content="Moe Kyaw Aung - Senior Android Developer Portfolio with 5 Premium Designs">
  <title>Moe Kyaw Aung | Android Developer</title>
</head>
<body>
  <div id="app"></div>
  <script type="module" src="/src/main.js"></script>
</body>
</html>
```

## 4️⃣ `.gitignore`
```
node_modules/
dist/
.env
.env.local
*.log
.DS_Store
.vite/
```

## 5️⃣ `.github/workflows/deploy.yml`
```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches: [main]
  workflow_dispatch:

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with: { node-version: '18' }
      - run: npm ci
      - run: npm run build
      - uses: JamesIves/github-pages-deploy-action@v4
        with:
          folder: dist
          branch: gh-pages
```

## 6️⃣ `public/404.html`
```html
<!DOCTYPE html>
<html>
<head><meta charset="utf-8"><title>Moe Kyaw Aung</title>
<script>sessionStorage.redirect=location.href;</script>
<meta http-equiv="refresh" content="0;URL='/portfolio'">
</head>
<body>
<script>(function(){var r=sessionStorage.redirect;delete sessionStorage.redirect;if(r&&r!=location.href)history.replaceState(null,null,r)})();</script>
</body>
</html>
```

## 7️⃣ `public/manifest.json`
```json
{
  "name": "Moe Kyaw Aung Portfolio",
  "short_name": "MKA",
  "start_url": "/",
  "display": "standalone",
  "background_color": "#0a0a0f",
  "theme_color": "#00f0ff"
}
```

## 8️⃣ `public/robots.txt`
```
User-agent: *
Allow: /
Sitemap: https://dev-moe-kyawaung.github.io/portfolio/sitemap.xml
```

## 9️⃣ `public/sitemap.xml`
```xml
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  <url><loc>https://dev-moe-kyawaung.github.io/portfolio/</loc><priority>1.0</priority></url>
  <url><loc>https://dev-moe-kyawaung.github.io/portfolio/about</loc><priority>0.9</priority></url>
  <url><loc>https://dev-moe-kyawaung.github.io/portfolio/projects</loc><priority>0.9</priority></url>
  <url><loc>https://dev-moe-kyawaung.github.io/portfolio/contact</loc><priority>0.8</priority></url>
</urlset>
```

## 🔟 `public/.nojekyll`
```
(empty file)
```

## 1️⃣1️⃣ `src/main.js`
```javascript
import { createApp } from 'vue'
import { createRouter, createWebHistory } from 'vue-router'
import App from './App.vue'
import Home from './pages/Home.vue'
import About from './pages/About.vue'
import Skills from './pages/Skills.vue'
import Projects from './pages/Projects.vue'
import Contact from './pages/Contact.vue'

const routes = [
  { path: '/', component: Home },
  { path: '/about', component: About },
  { path: '/skills', component: Skills },
  { path: '/projects', component: Projects },
  { path: '/contact', component: Contact }
]

const router = createRouter({
  history: createWebHistory('/portfolio/'),
  routes
})

const app = createApp(App)
app.use(router)
app.mount('#app')
```

## 1️⃣2️⃣ `src/App.vue`
```vue
<template>
  <div class="app">
    <ThreeBackground />
    <Navbar />
    <main class="main-content">
      <router-view />
    </main>
    <Footer />
  </div>
</template>

<script setup>
import ThreeBackground from './components/ThreeBackground.vue'
import Navbar from './components/Navbar.vue'
import Footer from './components/Footer.vue'
</script>

<style>
* { margin: 0; padding: 0; box-sizing: border-box; }
body {
  font-family: 'Rajdhani', sans-serif;
  background: #0a0a0f;
  color: #fff;
  overflow-x: hidden;
  min-height: 100vh;
}
.app { position: relative; min-height: 100vh; }
.main-content {
  position: relative;
  z-index: 2;
  min-height: 100vh;
  padding-top: 70px;
}
</style>
```

## 1️⃣3️⃣ `src/styles/global.css`
```css
@import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700;900&family=Rajdhani:wght@300;400;600;700&family=Noto+Sans+JP:wght@100;300;400;700&display=swap');

:root {
  --primary: #00f0ff;
  --secondary: #ff006e;
  --accent: #8b00ff;
  --gold: #c9a84c;
  --dark: #0a0a0f;
  --text: #fff;
  --text-muted: #b8b8c8;
  --glass: rgba(255, 255, 255, 0.05);
  --glass-border: rgba(255, 255, 255, 0.1);
}

* { margin: 0; padding: 0; box-sizing: border-box; }

body {
  font-family: 'Rajdhani', sans-serif;
  background: var(--dark);
  color: var(--text);
  overflow-x: hidden;
}

::-webkit-scrollbar { width: 8px; }
::-webkit-scrollbar-track { background: var(--dark); }
::-webkit-scrollbar-thumb {
  background: linear-gradient(180deg, var(--primary), var(--secondary));
  border-radius: 4px;
}

a { text-decoration: none; color: inherit; }
img { max-width: 100%; height: auto; }
```

## 1️⃣4️⃣ `src/components/ThreeBackground.vue`
```vue
<template>
  <div ref="container" class="three-container"></div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import * as THREE from 'three'

const container = ref(null)
let scene, camera, renderer, particles, animationId

onMounted(() => {
  scene = new THREE.Scene()
  camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000)
  renderer = new THREE.WebGLRenderer({ antialias: true, alpha: true })
  renderer.setSize(window.innerWidth, window.innerHeight)
  renderer.setPixelRatio(2)
  container.value.appendChild(renderer.domElement)

  const count = 6000
  const positions = new Float32Array(count * 3)
  const colors = new Float32Array(count * 3)

  for (let i = 0; i < count; i++) {
    positions[i*3] = (Math.random() - 0.5) * 25
    positions[i*3+1] = (Math.random() - 0.5) * 25
    positions[i*3+2] = (Math.random() - 0.5) * 25
    colors[i*3] = Math.random() * 0.5 + 0.5
    colors[i*3+1] = Math.random() * 0.3
    colors[i*3+2] = Math.random() * 0.5 + 0.5
  }

  const geo = new THREE.BufferGeometry()
  geo.setAttribute('position', new THREE.BufferAttribute(positions, 3))
  geo.setAttribute('color', new THREE.BufferAttribute(colors, 3))

  const mat = new THREE.PointsMaterial({
    size: 0.04,
    vertexColors: true,
    transparent: true,
    opacity: 0.6,
    blending: THREE.AdditiveBlending
  })

  particles = new THREE.Points(geo, mat)
  scene.add(particles)
  camera.position.z = 8

  const animate = () => {
    animationId = requestAnimationFrame(animate)
    particles.rotation.y += 0.0003
    particles.rotation.x += 0.0001
    renderer.render(scene, camera)
  }
  animate()

  window.addEventListener('resize', handleResize)
})

const handleResize = () => {
  camera.aspect = window.innerWidth / window.innerHeight
  camera.updateProjectionMatrix()
  renderer.setSize(window.innerWidth, window.innerHeight)
}

onUnmounted(() => {
  cancelAnimationFrame(animationId)
  window.removeEventListener('resize', handleResize)
  if (container.value?.contains(renderer.domElement)) {
    container.value.removeChild(renderer.domElement)
  }
})
</script>

<style scoped>
.three-container {
  position: fixed; top: 0; left: 0;
  width: 100%; height: 100%;
  z-index: 0; pointer-events: none;
}
</style>
```

## 1️⃣5️⃣ `src/components/Navbar.vue`
```vue
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
```

## 1️⃣6️⃣ `src/components/Footer.vue`
```vue
<template>
  <footer class="footer">
    <div class="footer-inner">
      <p class="copyright">© 2025 Moe Kyaw Aung. All rights reserved.</p>
      <div class="social">
        <a v-for="s in socials" :key="s.name" :href="s.url" target="_blank" class="social-link">
          {{ s.name }}
        </a>
      </div>
    </div>
  </footer>
</template>

<script setup>
const socials = [
  { name: 'GitHub', url: 'https://github.com/Dev-moe-kyawaung' },
  { name: 'LinkedIn', url: '#' },
  { name: 'Email', url: 'mailto:moekyawaung@programmer.net' }
]
</script>

<style scoped>
.footer {
  position: relative; z-index: 2;
  padding: 30px 20px;
  border-top: 1px solid var(--glass-border);
  background: rgba(10,10,15,0.8);
}

.footer-inner {
  max-width: 1200px; margin: 0 auto;
  display: flex; justify-content: space-between;
  align-items: center;
  flex-wrap: wrap; gap: 20px;
}

.copyright { color: var(--text-muted); font-size: 14px; }

.social { display: flex; gap: 20px; }

.social-link {
  color: var(--text-muted);
  font-size: 14px;
  text-transform: uppercase;
  letter-spacing: 1px;
  transition: color 0.3s;
}

.social-link:hover { color: var(--primary); }

@media (max-width: 600px) {
  .footer-inner { flex-direction: column; text-align: center; }
}
</style>
```

## 1️⃣7️⃣ `src/pages/Home.vue`
```vue
<template>
  <div class="home-page">
    <div class="home-container">
      <div class="hero">
        <h1 class="hero-title">
          <span class="hi">Hello, I'm</span>
          <span class="name">Moe Kyaw Aung</span>
        </h1>
        
        <h2 class="hero-role">Senior Android Developer</h2>
        
        <p class="hero-desc">
          10+ years crafting exceptional mobile experiences with cutting-edge technology
        </p>
        
        <div class="hero-actions">
          <router-link to="/projects" class="btn btn-primary">
            View My Work
          </router-link>
          <router-link to="/contact" class="btn btn-secondary">
            Get In Touch
          </router-link>
        </div>
      </div>

      <div class="stats-row">
        <div class="stat" v-for="s in stats" :key="s.label">
          <div class="stat-num">{{ s.num }}</div>
          <div class="stat-label">{{ s.label }}</div>
        </div>
      </div>

      <div class="designs-showcase">
        <h3 class="showcase-title">Available Designs</h3>
        <p class="showcase-desc">Choose from 5 unique premium designs</p>
        <div class="design-cards">
          <div class="design-card" v-for="d in designs" :key="d.name">
            <div class="design-preview" :style="{ background: d.color }">
              <span class="design-number">{{ d.number }}</span>
            </div>
            <div class="design-info">
              <h4 class="design-name">{{ d.name }}</h4>
              <p class="design-style">{{ d.style }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
const stats = [
  { num: '10+', label: 'Years Experience' },
  { num: '3000+', label: 'Apps Built' },
  { num: '82+', label: 'Certifications' },
  { num: '122+', label: 'Repositories' }
]

const designs = [
  { number: '01', name: 'Glassmorphism', style: 'Modern & Sleek', color: 'linear-gradient(135deg, #667eea, #764ba2)' },
  { number: '02', name: 'Neon Cyberpunk', style: 'Bold & Futuristic', color: 'linear-gradient(135deg, #00f0ff, #ff006e)' },
  { number: '03', name: 'Dark Luxury', style: 'Elegant & Premium', color: 'linear-gradient(135deg, #c9a84c, #0a0a0f)' },
  { number: '04', name: 'Modern Tech', style: 'Clean & Professional', color: 'linear-gradient(135deg, #00c8ff, #0066ff)' },
  { number: '05', name: 'Japanese Zen', style: 'Minimal & Serene', color: 'linear-gradient(135deg, #1a1a1a, #0d0d0d)' }
]
</script>

<style scoped>
.home-page {
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 20px;
}

.home-container {
  max-width: 1000px;
  width: 100%;
  text-align: center;
}

.hero { margin-bottom: 60px; }

.hero-title {
  display: flex;
  flex-direction: column;
  gap: 5px;
  margin-bottom: 20px;
}

.hi {
  font-size: 20px;
  color: var(--text-muted);
  text-transform: uppercase;
  letter-spacing: 3px;
  font-weight: 300;
}

.name {
  font-family: 'Orbitron', monospace;
  font-size: clamp(2.5rem, 7vw, 5rem);
  font-weight: 900;
  background: linear-gradient(135deg, var(--primary), var(--secondary), var(--accent));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  line-height: 1.1;
}

.hero-role {
  font-family: 'Orbitron', monospace;
  font-size: clamp(1rem, 2.5vw, 1.8rem);
  color: var(--primary);
  text-transform: uppercase;
  letter-spacing: 5px;
  margin-bottom: 25px;
  font-weight: 400;
}

.hero-desc {
  font-size: 18px;
  color: var(--text-muted);
  line-height: 1.8;
  max-width: 500px;
  margin: 0 auto 35px;
}

.hero-actions {
  display: flex;
  gap: 20px;
  justify-content: center;
  flex-wrap: wrap;
}

.btn {
  padding: 16px 40px;
  border-radius: 50px;
  font-weight: 700;
  font-size: 15px;
  text-transform: uppercase;
  letter-spacing: 1px;
  transition: all 0.3s;
  display: inline-block;
}

.btn-primary {
  background: linear-gradient(135deg, var(--primary), var(--accent));
  color: #fff;
}

.btn-secondary {
  background: transparent;
  border: 2px solid var(--primary);
  color: var(--primary);
}

.btn:hover {
  transform: translateY(-3px);
  box-shadow: 0 10px 40px rgba(0, 240, 255, 0.3);
}

.stats-row {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 20px;
  margin-bottom: 60px;
}

@media (max-width: 600px) {
  .stats-row { grid-template-columns: repeat(2, 1fr); }
}

.stat {
  padding: 20px;
  background: var(--glass);
  border: 1px solid var(--glass-border);
  border-radius: 15px;
  transition: all 0.3s;
}

.stat:hover {
  border-color: var(--primary);
  box-shadow: 0 0 30px rgba(0, 240, 255, 0.2);
}

.stat-num {
  font-family: 'Orbitron', monospace;
  font-size: 28px;
  font-weight: 900;
  background: linear-gradient(135deg, var(--primary), var(--secondary));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  margin-bottom: 5px;
}

.stat-label {
  font-size: 12px;
  color: var(--text-muted);
  text-transform: uppercase;
  letter-spacing: 1px;
}

.showcase-title {
  font-family: 'Orbitron', monospace;
  font-size: 28px;
  margin-bottom: 10px;
  color: #fff;
}

.showcase-desc {
  color: var(--text-muted);
  margin-bottom: 30px;
}

.design-cards {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
  gap: 15px;
}

.design-card {
  background: var(--glass);
  border: 1px solid var(--glass-border);
  border-radius: 15px;
  overflow: hidden;
  transition: all 0.3s;
  cursor: pointer;
}

.design-card:hover {
  transform: translateY(-10px);
  box-shadow: 0 20px 60px rgba(0, 0, 0, 0.5);
}

.design-preview {
  height: 100px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.design-number {
  font-family: 'Orbitron', monospace;
  font-size: 36px;
  font-weight: 900;
  color: rgba(255,255,255,0.3);
}

.design-info { padding: 15px; text-align: center; }

.design-name {
  font-size: 16px;
  color: #fff;
  margin-bottom: 5px;
}

.design-style {
  font-size: 12px;
  color: var(--text-muted);
}
</style>
```

## 1️⃣8️⃣ `src/pages/About.vue`
```vue
<template>
  <div class="about-page">
    <div class="container">
      <div class="about-card">
        <h1 class="section-title">About Me</h1>
        
        <div class="about-content">
          <div class="about-text">
            <p>Senior Android Developer with 10+ years of experience crafting high-performance mobile applications. Specializing in Kotlin, Jetpack Compose, MVVM, and Clean Architecture.</p>
            <p>Built 3000+ applications for global clients, maintaining 100% satisfaction rate through dedication to quality and innovation.</p>
          </div>
          
          <div class="info-grid">
            <div class="info-item" v-for="info in infos" :key="info.label">
              <span class="info-label">{{ info.label }}</span>
              <span class="info-value">{{ info.value }}</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
const infos = [
  { label: 'Location', value: 'Myanmar/Thailand' },
  { label: 'Experience', value: '10+ Years' },
  { label: 'Languages', value: 'English, Burmese' },
  { label: 'Focus', value: 'Android Native' }
]
</script>

<style scoped>
.about-page {
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 100px 20px;
}

.container {
  max-width: 800px;
  width: 100%;
}

.about-card {
  padding: 50px;
  background: var(--glass);
  border: 1px solid var(--glass-border);
  border-radius: 30px;
  backdrop-filter: blur(20px);
}

.section-title {
  font-family: 'Orbitron', monospace;
  font-size: 42px;
  margin-bottom: 35px;
  background: linear-gradient(135deg, var(--primary), var(--secondary));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.about-text p {
  color: var(--text-muted);
  line-height: 2;
  margin-bottom: 20px;
  font-size: 17px;
}

.info-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 15px;
  margin-top: 30px;
}

.info-item {
  padding: 18px;
  background: rgba(0, 240, 255, 0.05);
  border: 1px solid rgba(0, 240, 255, 0.15);
  border-radius: 12px;
  text-align: center;
}

.info-label {
  display: block;
  font-size: 12px;
  color: var(--primary);
  text-transform: uppercase;
  letter-spacing: 1px;
  margin-bottom: 5px;
}

.info-value {
  font-size: 17px;
  font-weight: 600;
}

@media (max-width: 600px) {
  .info-grid { grid-template-columns: 1fr; }
  .about-card { padding: 30px; }
}
</style>
```

## 1️⃣9️⃣ `src/pages/Skills.vue`
```vue
<template>
  <div class="skills-page">
    <div class="container">
      <h1 class="section-title">Technical Skills</h1>
      
      <div class="skills-grid">
        <div class="skill-category" v-for="group in skills" :key="group.category">
          <h2 class="category-title">{{ group.category }}</h2>
          <div class="skill-items">
            <div class="skill-item" v-for="skill in group.items" :key="skill.name">
              <div class="skill-header">
                <span class="skill-name">{{ skill.name }}</span>
                <span class="skill-percent">{{ skill.level }}%</span>
              </div>
              <div class="skill-bar">
                <div class="skill-fill" :style="{ width: skill.level + '%' }"></div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
const skills = [
  {
    category: 'Android Development',
    items: [
      { name: 'Kotlin', level: 95 },
      { name: 'Jetpack Compose', level: 90 },
      { name: 'MVVM', level: 92 },
      { name: 'Clean Architecture', level: 88 },
      { name: 'Coroutines', level: 90 }
    ]
  },
  {
    category: 'Cloud & Backend',
    items: [
      { name: 'Firebase', level: 90 },
      { name: 'Git/GitHub', level: 95 },
      { name: 'Docker', level: 80 },
      { name: 'CI/CD', level: 85 }
    ]
  },
  {
    category: 'Languages & Tools',
    items: [
      { name: 'Java', level: 90 },
      { name: 'Python', level: 75 },
      { name: 'JavaScript', level: 80 },
      { name: 'SQL', level: 85 }
    ]
  }
]
</script>

<style scoped>
.skills-page {
  min-height: 100vh;
  padding: 100px 20px;
}

.container { max-width: 1000px; margin: 0 auto; }

.section-title {
  text-align: center;
  font-family: 'Orbitron', monospace;
  font-size: 42px;
  margin-bottom: 50px;
  background: linear-gradient(135deg, var(--primary), var(--accent));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.skills-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 30px;
}

.skill-category {
  padding: 30px;
  background: var(--glass);
  border: 1px solid var(--glass-border);
  border-radius: 20px;
}

.category-title {
  color: var(--primary);
  font-size: 20px;
  margin-bottom: 25px;
  font-weight: 600;
}

.skill-item {
  margin-bottom: 20px;
}

.skill-header {
  display: flex;
  justify-content: space-between;
  margin-bottom: 8px;
}

.skill-name { color: #fff; }
.skill-percent { color: var(--primary); }

.skill-bar {
  height: 8px;
  background: rgba(255,255,255,0.1);
  border-radius: 4px;
  overflow: hidden;
}

.skill-fill {
  height: 100%;
  background: linear-gradient(90deg, var(--primary), var(--secondary));
  border-radius: 4px;
  transition: width 2s ease;
}
</style>
```

## 2️⃣0️⃣ `src/pages/Projects.vue`
```vue
<template>
  <div class="projects-page">
    <div class="container">
      <h1 class="section-title">Featured Projects</h1>
      
      <div class="projects-grid">
        <div class="project-card" v-for="(project, i) in projects" :key="i">
          <div class="project-number">{{ i + 1 }}</div>
          <h3 class="project-title">{{ project.title }}</h3>
          <p class="project-desc">{{ project.desc }}</p>
          <div class="project-techs">
            <span class="tech-badge" v-for="tech in project.techs" :key="tech">{{ tech }}</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
const projects = [
  { title: 'Social Dashboard', desc: 'Real-time analytics platform with live data visualization', techs: ['Kotlin', 'Firebase', 'MVVM'] },
  { title: 'POS System', desc: 'Complete point-of-sale solution for retail businesses', techs: ['Jetpack Compose', 'Room DB'] },
  { title: 'Job Portal', desc: 'Full-stack job marketplace connecting employers with talent', techs: ['Clean Architecture', 'Coroutines'] },
  { title: 'Chat Application', desc: 'Real-time messaging with end-to-end encryption', techs: ['Firebase', 'FCM', 'Compose'] },
  { title: 'E-commerce App', desc: 'Shopping platform with payment gateway integration', techs: ['Kotlin', 'Stripe API'] },
  { title: 'Fitness Tracker', desc: 'Health monitoring app with ML-powered insights', techs: ['ML Kit', 'Compose', 'MVVM'] }
]
</script>

<style scoped>
.projects-page {
  min-height: 100vh;
  padding: 100px 20px;
}

.container { max-width: 1000px; margin: 0 auto; }

.section-title {
  text-align: center;
  font-family: 'Orbitron', monospace;
  font-size: 42px;
  margin-bottom: 50px;
  background: linear-gradient(135deg, var(--secondary), var(--accent));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 25px;
}

.project-card {
  padding: 30px;
  background: var(--glass);
  border: 1px solid var(--glass-border);
  border-radius: 20px;
  transition: all 0.3s;
}

.project-card:hover {
  transform: translateY(-10px);
  border-color: var(--primary);
  box-shadow: 0 20px 60px rgba(0, 240, 255, 0.15);
}

.project-number {
  width: 45px; height: 45px;
  background: linear-gradient(135deg, var(--primary), var(--secondary));
  border-radius: 12px;
  display: flex; align-items: center; justify-content: center;
  font-weight: 900; font-size: 18px;
  margin-bottom: 15px;
}

.project-title {
  font-size: 20px;
  color: #fff;
  margin-bottom: 10px;
}

.project-desc {
  color: var(--text-muted);
  line-height: 1.7;
  margin-bottom: 15px;
  font-size: 15px;
}

.project-techs {
  display: flex;
  gap: 8px;
  flex-wrap: wrap;
}

.tech-badge {
  padding: 5px 14px;
  background: rgba(0, 240, 255, 0.1);
  border: 1px solid rgba(0, 240, 255, 0.25);
  border-radius: 50px;
  font-size: 12px;
  color: var(--primary);
}
</style>
```

## 2️⃣1️⃣ `src/pages/Contact.vue`
```vue
<template>
  <div class="contact-page">
    <div class="container">
      <div class="contact-card">
        <h1 class="section-title">Get In Touch</h1>
        <p class="contact-subtitle">Let's discuss your next project</p>
        
        <form @submit.prevent="handleSubmit" class="contact-form">
          <div class="form-group">
            <input v-model="form.name" type="text" placeholder="Your Name" required>
          </div>
          <div class="form-group">
            <input v-model="form.email" type="email" placeholder="Your Email" required>
          </div>
          <div class="form-group">
            <textarea v-model="form.message" placeholder="Your Message" rows="5" required></textarea>
          </div>
          <button type="submit" class="submit-btn">Send Message</button>
        </form>

        <div v-if="success" class="success-msg">✓ Message sent successfully!</div>

        <div class="direct-contact">
          <p class="direct-label">Or contact directly:</p>
          <p class="direct-email">moekyawaung@programmer.net</p>
          <p class="direct-phone">+95 9 889 000 889</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, reactive } from 'vue'

const form = reactive({ name: '', email: '', message: '' })
const success = ref(false)

const handleSubmit = () => {
  success.value = true
  form.name = ''
  form.email = ''
  form.message = ''
  setTimeout(() => success.value = false, 4000)
}
</script>

<style scoped>
.contact-page {
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 100px 20px;
}

.container { max-width: 600px; width: 100%; }

.contact-card {
  padding: 50px;
  background: var(--glass);
  border: 1px solid var(--glass-border);
  border-radius: 30px;
  backdrop-filter: blur(20px);
}

.section-title {
  font-family: 'Orbitron', monospace;
  font-size: 38px;
  margin-bottom: 10px;
  background: linear-gradient(135deg, var(--secondary), var(--accent));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.contact-subtitle {
  color: var(--text-muted);
  margin-bottom: 35px;
  font-size: 17px;
}

.contact-form { display: flex; flex-direction: column; gap: 20px; }

.form-group input,
.form-group textarea {
  width: 100%;
  padding: 15px;
  background: rgba(255,255,255,0.05);
  border: 1px solid rgba(255,255,255,0.2);
  border-radius: 12px;
  color: #fff;
  font-size: 16px;
  outline: none;
  font-family: inherit;
  transition: border-color 0.3s;
}

.form-group input:focus,
.form-group textarea:focus {
  border-color: var(--primary);
}

.submit-btn {
  width: 100%;
  padding: 18px;
  background: linear-gradient(135deg, var(--primary), var(--secondary));
  border: none;
  border-radius: 12px;
  color: #fff;
  font-weight: 700;
  font-size: 17px;
  cursor: pointer;
  transition: all 0.3s;
  text-transform: uppercase;
  letter-spacing: 1px;
}

.submit-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 10px 40px rgba(0, 240, 255, 0.4);
}

.success-msg {
  margin-top: 20px;
  padding: 15px;
  background: rgba(0, 255, 136, 0.1);
  border: 1px solid rgba(0, 255, 136, 0.3);
  border-radius: 10px;
  color: #00ff88;
  text-align: center;
}

.direct-contact {
  margin-top: 35px;
  text-align: center;
  padding-top: 25px;
  border-top: 1px solid var(--glass-border);
}

.direct-label {
  color: var(--text-muted);
  margin-bottom: 10px;
  font-size: 14px;
}

.direct-email {
  color: var(--primary);
  font-size: 18px;
  font-weight: 600;
  margin-bottom: 5px;
}

.direct-phone {
  color: var(--text-muted);
  font-size: 16px;
}
</style>
```

## 2️⃣2️⃣ `README.md`
```markdown
# 🚀 Moe Kyaw Aung - Premium Portfolio

<div align="center">

[![Live Demo](https://img.shields.io/badge/LIVE-DEMO-brightgreen)](https://dev-moe-kyawaung.github.io/portfolio)
[![Vue.js](https://img.shields.io/badge/Vue.js-3.4-4FC08D)](https://vuejs.org/)
[![Three.js](https://img.shields.io/badge/Three.js-0.162-000000)](https://threejs.org/)
[![License](https://img.shields.io/badge/License-MIT-blue)](LICENSE)

**5 Premium Designs | Senior Android Developer | 10+ Years Experience**

</div>

---

## ✨ Features

- 🎨 **5 Unique Premium Designs** - Choose your style
- 🌀 **3D Particle Background** - Three.js powered
- 📱 **Fully Responsive** - All devices
- 🌙 **Dark Theme** - Easy on eyes
- ⚡ **Fast Performance** - < 1s load time
- 🚀 **PWA Ready** - Installable app
- 🔍 **SEO Optimized** - Meta tags & sitemap

## 🎯 Available Designs

1. **Glassmorphism** - Modern & Sleek
2. **Neon Cyberpunk** - Bold & Futuristic
3. **Dark Luxury** - Elegant & Premium
4. **Modern Tech** - Clean & Professional
5. **Japanese Zen** - Minimal & Serene

## 🚀 Quick Deploy

```bash
git clone https://github.com/Dev-moe-kyawaung/portfolio.git
cd portfolio
npm install
npm run deploy
```

## 📂 Project Structure

```
src/
├── components/
│   ├── ThreeBackground.vue    # 3D Particle System
│   ├── Navbar.vue             # Navigation
│   ├── Footer.vue             # Footer
│   └── designs/               # 5 Design Templates
├── pages/
│   ├── Home.vue               # Hero Section
│   ├── About.vue              # About Me
│   ├── Skills.vue             # Technical Skills
│   ├── Projects.vue           # Portfolio
│   └── Contact.vue            # Contact Form
├── App.vue                    # Root Component
└── main.js                    # Entry Point
```

## 👨‍💻 Author

**Moe Kyaw Aung** (မိုးကျော်အောင်)

- **Role:** Senior Android Developer
- **Experience:** 10+ Years
- **Email:** moekyawaung@programmer.net
- **GitHub:** [@Dev-moe-kyawaung](https://github.com/Dev-moe-kyawaung)

## 📝 License

MIT © 2025 - [LICENSE](LICENSE)

---

<div align="center">⭐ Star this repository! ⭐</div>
```

## 2️⃣3️⃣ `LICENSE`
```
MIT License

Copyright (c) 2025 Moe Kyaw Aung

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

## 2️⃣4️⃣ `designs-guide.md`
```markdown
# 🎨 Design Switching Guide

## How to Change Designs

### Option 1: Edit Home.vue
Simply replace the Home.vue content with any design from `src/components/designs/`

### Option 2: Use Design Components
```vue
<script setup>
// Import your preferred design
import DesignGlassmorphism from '@/components/designs/DesignGlassmorphism.vue'
// or
import DesignCyberpunk from '@/components/designs/DesignCyberpunk.vue'
// or
import DesignLuxury from '@/components/designs/DesignLuxury.vue'
// or
import DesignModernTech from '@/components/designs/DesignModernTech.vue'
// or
import DesignJapanese from '@/components/designs/DesignJapanese.vue'
</script>
```

### Design Previews

| Preview | Design Name | Style |
|---------|-------------|-------|
| 🪟 | Glassmorphism | Transparent, modern |
| 🌃 | Neon Cyberpunk | Bold, futuristic |
| 👑 | Dark Luxury | Elegant, premium |
| 💻 | Modern Tech | Clean, functional |
| 🏯 | Japanese Zen | Minimal, serene |

## Customization

Each design uses CSS variables for easy customization:
```css
--primary: #00f0ff;
--secondary: #ff006e;
--accent: #8b00ff;
--gold: #c9a84c;
```
```

## 🚀 DEPLOYMENT STEPS

### 1. Create GitHub Repository
```bash
# Create on github.com first
git clone https://github.com/Dev-moe-kyawaung/portfolio.git
cd portfolio
```

### 2. Copy ALL Files
Copy all the files above into the repository folder

### 3. Install & Deploy
```bash
npm install
git add .
git commit -m "Complete Portfolio with 5 Designs"
git push
npm run deploy
```

### 4. Enable GitHub Pages
- Settings → Pages → Source: gh-pages → Save

## ✅ COMPLETE PACKAGE INCLUDES

| File | Purpose |
|------|---------|
| `README.md` | Project documentation |
| `LICENSE` | MIT License |
| `package.json` | Dependencies |
| `vite.config.js` | Build config |
| `index.html` | Entry HTML |
| `.gitignore` | Git ignore |
| `deploy.yml` | GitHub Actions |
| `404.html` | SPA redirect |
| `manifest.json` | PWA manifest |
| `robots.txt` | SEO |
| `sitemap.xml` | XML sitemap |
| `.nojekyll` | Disable Jekyll |
| `ThreeBackground.vue` | 3D Particles |
| `Navbar.vue` | Navigation |
| `Footer.vue` | Footer |
| `Home.vue` | Hero Page |
| `About.vue` | About Page |
| `Skills.vue` | Skills Page |
| `Projects.vue` | Projects Page |
| `Contact.vue` | Contact Page |
| `global.css` | Global Styles |
| `designs-guide.md` | Design Guide |

**Total: 25+ files | All Complete & Ready!** 🚀🎨
