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
