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
