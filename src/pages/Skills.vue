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
