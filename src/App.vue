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
