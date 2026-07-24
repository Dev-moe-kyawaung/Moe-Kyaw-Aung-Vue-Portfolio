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
