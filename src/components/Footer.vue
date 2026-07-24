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
